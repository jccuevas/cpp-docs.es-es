---
title: Archivos DLL y comportamiento de la biblioteca de tiempo de ejecución de Visual C++
ms.date: 05/06/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
ms.openlocfilehash: d3f3197b6b7b01e7f69767b72286d6d21470cb0e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217755"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Archivos DLL y comportamiento de la biblioteca de tiempo de ejecución de Visual C++

Cuando se compila una biblioteca de vínculos dinámicos (DLL) mediante el uso de Visual Studio, de forma predeterminada, el vinculador incluye el objeto Visual C++ biblioteca en tiempo de ejecución (VCRuntime). VCRuntime contiene código necesario para inicializar y finalizar un ejecutable de C o C++. Cuando se vincula a un archivo DLL, el código de VCRuntime proporciona una función de punto de entrada DLL interna denominada `_DllMainCRTStartup` que controla los mensajes de sistema operativo de Windows para el archivo DLL para asociar o desasociar un proceso o subproceso. El `_DllMainCRTStartup` función realiza tareas esenciales como la seguridad de búfer de pila configurado, inicialización de la biblioteca en tiempo de ejecución (CRT) de C y la finalización y llama a los constructores y destructores para los objetos globales y estáticos. `_DllMainCRTStartup` También llama a funciones de otras bibliotecas como WinRT, MFC y ATL para realizar su propia inicialización y terminación de enlace. Sin esta inicialización, CRT y otras bibliotecas, así como las variables estáticas, podría quedar en un estado no inicializado. Se llama a si el archivo DLL usa un CRT vinculado estáticamente o un archivo DLL de CRT vinculado dinámicamente la misma inicialización de VCRuntime interna y rutinas de terminación.

## <a name="default-dll-entry-point-dllmaincrtstartup"></a>_DllMainCRTStartup de punto de entrada DLL de forma predeterminada

En Windows, todos los archivos DLL pueden contener una función de punto de entrada opcional, normalmente denominada `DllMain`, que se llama para la inicialización y terminación. Esto le ofrece la oportunidad de asignar o liberar recursos adicionales según sea necesario. Windows llama a la función de punto de entrada en cuatro situaciones: asociación de proceso, desasociación de procesos, asociación de subproceso y desasociación de subproceso. Cuando se carga una DLL en un espacio de direcciones de proceso cuando se carga una aplicación que lo utiliza, o cuando la aplicación solicita el archivo DLL en tiempo de ejecución, el sistema operativo crea una copia independiente de los datos del archivo DLL. Esto se denomina *proceso adjuntar*. *Asociación de subproceso* se produce cuando el proceso de cargar la DLL en crea un nuevo subproceso. *Desasociación de subproceso* se produce cuando finaliza el subproceso, y *desasociar proceso* es cuando el archivo DLL ya no es necesario y se publica una aplicación. El sistema operativo hace una llamada al punto de entrada de archivo DLL independiente para cada uno de estos eventos, pasando un *motivo* argumento para cada tipo de evento. Por ejemplo, el sistema operativo envía `DLL_PROCESS_ATTACH` como el *motivo* argumento para indicar el proceso de adjuntar.

La biblioteca de VCRuntime proporciona una función de punto de entrada denominada `_DllMainCRTStartup` para controlar las operaciones de inicialización y terminación de forma predeterminada. En el proceso de adjuntar, el `_DllMainCRTStartup` función configura las comprobaciones de seguridad de búfer, inicializa el CRT y otras bibliotecas, inicializa la información de tipo en tiempo de ejecución, inicializa y llama a constructores para datos estáticos y no local, inicializa el almacenamiento local de subprocesos , incrementa un contador interno estático para cada operación de adjuntar y, a continuación, llama a un usuario o biblioteca-proporcionado por `DllMain`. En el proceso de desasociación, la función se lleva a cabo estos pasos en orden inverso. Llama a `DllMain`, disminuye el contador interno, llama a los destructores, la terminación de CRT las llamadas a funciones y registrado `atexit` funciones y notifica a cualquier otra biblioteca de terminación. Cuando el contador de los datos adjuntos se llega a cero, la función devuelve `FALSE` para indicar a Windows que se puede descargar el archivo DLL. El `_DllMainCRTStartup` también se denomina función de subproceso durante la asociación y desasociación de subproceso. En estos casos, el código de VCRuntime no ninguna inicialización adicional ni la finalización por sí mismo y simplemente llama a `DllMain` para pasar el mensaje a lo largo. Si `DllMain` devuelve `FALSE` del proceso de adjuntar, error, de señalización `_DllMainCRTStartup` llamadas `DllMain` nuevo y pasa `DLL_PROCESS_DETACH` como el *motivo* argumento, a continuación, recorre el resto de la proceso de finalización.

Al compilar archivos DLL en Visual Studio, el punto de entrada predeterminado `_DllMainCRTStartup` proporcionado por VCRuntime se vinculará automáticamente. No es necesario especificar una función de punto de entrada para el archivo DLL mediante la [/Entry (símbolo de punto de entrada)](reference/entry-entry-point-symbol.md) opción del vinculador.

> [!NOTE]
> Aunque es posible especificar otra función de punto de entrada para un archivo DLL utilizando el/Entry: opción del vinculador, no se recomienda, ya que la función de punto de entrada tendría que duplicar todo lo que `_DllMainCRTStartup` es así, en el mismo orden. VCRuntime proporciona funciones que permiten duplicar su comportamiento. Por ejemplo, puede llamar a [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) inmediatamente en el proceso de adjuntar para admitir la [/GS (comprobación de seguridad de búfer)](reference/gs-buffer-security-check.md) opción de comprobación del búfer. Puede llamar a la `_CRT_INIT` función, pasando los mismos parámetros como la función de punto de entrada, para realizar el resto de las funciones de inicialización o de finalización de la DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicializar un archivo DLL

El archivo DLL puede tener código de inicialización que deberá ejecutarse cuando se cargue el archivo DLL. En orden para realizar sus propias funciones de inicialización y terminación de DLL, `_DllMainCRTStartup` llama a una función denominada `DllMain` que puede proporcionar. Su `DllMain` debe tener la firma requerida para un punto de entrada del archivo DLL. La función de punto de entrada predeterminado `_DllMainCRTStartup` llamadas `DllMain` usando los mismos parámetros pasados por Windows. De forma predeterminada, si no proporcionas un `DllMain` función, Visual Studio proporciona uno automáticamente y lo vincula en poder `_DllMainCRTStartup` siempre tiene que llamar. Esto significa que si no tiene que inicializar el archivo DLL, no hay nada especial que debe hacer al compilar el archivo DLL.

Se trata de la firma usada para `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Algunas bibliotecas de ajustan la `DllMain` función para usted. Por ejemplo, en una DLL de MFC regular, implemente el `CWinApp` del objeto `InitInstance` y `ExitInstance` funciones miembro para realizar la inicialización y terminación requeridas por la DLL. Para obtener más información, consulte el [regular inicializar archivos DLL de MFC](#initializing-regular-dlls) sección.

> [!WARNING]
> Existen límites significativos en lo que puede hacer con seguridad en un punto de entrada del archivo DLL. Consulte [procedimientos recomendados generales](/windows/desktop/Dlls/dynamic-link-library-best-practices) para las API específicas de Windows que no son seguras para llamar a en `DllMain`. Si tiene cualquier cosa menos, a continuación, la inicialización más sencilla que hacer en una función de inicialización para el archivo DLL. Puede exigir que las aplicaciones llamen a la función de inicialización después `DllMain` ha ejecución y antes de que llame a otras funciones en el archivo DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializar archivos DLL normales (no basados en MFC)

Para realizar su propia inicialización en archivos DLL normales (no basados en MFC) que usan VCRuntime proporcionado `_DllMainCRTStartup` punto de entrada, el código de origen del archivo DLL debe contener una función denominada `DllMain`. El código siguiente presenta una estructura básica que muestra lo que la definición de `DllMain` sería:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason)
    {
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```

> [!NOTE]
> Documentación del SDK de Windows anterior, se dice que se debe especificar el nombre real de la función de punto de entrada del archivo DLL en el vinculador de línea de comandos con la opción/Entry. Con Visual Studio, no es necesario usar la opción/ENTRY si el nombre de la función de punto de entrada es `DllMain`. De hecho, si usa la opción/Entry y el nombre de su punto de entrada función algo distinto `DllMain`, CRT no se inicializan correctamente a menos que la función de punto de entrada hace que las mismas llamadas de inicialización que `_DllMainCRTStartup` hace.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicializar archivos DLL de MFC estándar

Porque tiene archivos DLL de MFC estándar un `CWinApp` objeto, deben realizar sus tareas de inicialización y finalización en la misma ubicación que una aplicación MFC: en el `InitInstance` y `ExitInstance` funciones miembro de la DLL `CWinApp`-derivados clase. Dado que MFC proporciona una `DllMain` función que llama a `_DllMainCRTStartup` para `DLL_PROCESS_ATTACH` y `DLL_PROCESS_DETACH`, no debe escribir su propio `DllMain` función. MFC proporcionada por el `DllMain` llamadas de función `InitInstance` cuando se cargue el archivo DLL y llama a `ExitInstance` antes de descargar el archivo DLL.

Un archivo DLL MFC puede realizar un seguimiento de varios subprocesos mediante una llamada a [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc) y [TlsGetValue](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) en su `InitInstance` función. Estas funciones permiten que la DLL realizar un seguimiento de los datos específicos del subproceso.

En la DLL de MFC normal que se vincule dinámicamente a MFC, si está utilizando OLE de MFC, MFC base de datos (o DAO) o admitir Sockets de MFC, respectivamente, la depuración MFCO archivos DLL de extensión MFC*versión*D.dll, MFCD*versión*D.dll y MFCN*versión*D.dll (donde *versión* es el número de versión) se vinculan automáticamente. Debe llamar a una de las siguientes funciones de inicialización predefinidas para cada uno de estos archivos DLL que está usando en su MFC DLL regular `CWinApp::InitInstance`.

|Tipo de compatibilidad con MFC|Función de inicialización para llamar a|
|-------------------------|-------------------------------------|
|OLE de MFC (MFCO*versión*D.dll)|`AfxOleInitModule`|
|Base de datos de MFC (MFCD*versión*D.dll)|`AfxDbInitModule`|
|Sockets de MFC (MFCN*versión*D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicializar archivos DLL de extensión MFC

Porque los archivos DLL de extensión MFC no tienen un `CWinApp`-derivados de objeto (como archivos DLL de MFC estándar), debe agregar el código de inicialización y finalización para el `DllMain` función que genera el Asistente para archivos DLL de MFC.

El asistente proporciona el siguiente código para archivos DLL de extensión MFC. En el código, `PROJNAME` es un marcador de posición para el nombre del proyecto.

```cpp
#include "stdafx.h"
#include <afxdllx.h>

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      TRACE0("PROJNAME.DLL Initializing!\n");

      // MFC extension DLL one-time initialization
      AfxInitExtensionModule(PROJNAMEDLL,
                                 hInstance);

      // Insert this DLL into the resource chain
      new CDynLinkLibrary(Dll3DLL);
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      TRACE0("PROJNAME.DLL Terminating!\n");
   }
   return 1;   // ok
}
```

Crear un nuevo `CDynLinkLibrary` objeto durante la inicialización permite la extensión MFC DLL para exportar `CRuntimeClass` objetos o recursos a la aplicación cliente.

Si va a usar la extensión MFC DLL desde archivos DLL de MFC estándar de uno o más, debe exportar una función de inicialización que se crea un `CDynLinkLibrary` objeto. Esa función debe llamarse desde cada una de las DLL de MFC regulares que utilizan el archivo DLL de extensión MFC. Es un lugar adecuado para llamar a esta función de inicialización en el `InitInstance` función miembro de la MFC DLL regular `CWinApp`-objeto derivado antes de la DLL de extensión MFC clases o funciones exportadas.

En el `DllMain` que genera el Asistente para archivos DLL de MFC, la llamada a `AfxInitExtensionModule` captura clases en tiempo de ejecución del módulo (`CRuntimeClass` estructuras), así como los generadores de objetos (`COleObjectFactory` objetos) para usar cuando el `CDynLinkLibrary` se crea el objeto. Debe comprobar el valor devuelto de `AfxInitExtensionModule`; si devuelve un valor de cero `AfxInitExtensionModule`, devuelven cero desde su `DllMain` función.

Si el archivo DLL de extensión MFC se vinculará explícitamente a un archivo ejecutable (lo que significa que el ejecutable llama `AfxLoadLibrary` para vincular al archivo DLL), debe agregar una llamada a `AfxTermExtensionModule` en `DLL_PROCESS_DETACH`. Esta función permite MFC limpiar el archivo DLL de extensión MFC cuando cada proceso se separa de la DLL de extensión MFC (lo que ocurre cuando se cierra el proceso o cuando se descarga el archivo DLL como resultado de una `AfxFreeLibrary` llamar). Si el archivo DLL de extensión MFC se vinculará implícitamente a la aplicación, la llamada a `AfxTermExtensionModule` no es necesario.

Las aplicaciones que se debe llamar explícitamente vincular a archivos DLL de extensión MFC `AfxTermExtensionModule` al liberar la DLL. También deben usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de las funciones de Win32 `LoadLibrary` y `FreeLibrary`) si la aplicación utiliza varios subprocesos. Uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando la extensión se carga y descarga el archivo DLL de MFC no dañe el estado global de MFC.

Dado que MFCx0.dll está completamente inicializado en el momento en `DllMain` es llamado, puede asignar memoria y llamar a funciones MFC dentro `DllMain` (a diferencia de la versión de 16 bits de MFC).

Archivos DLL de extensión pueden ocuparse de multithreading controlando el `DLL_THREAD_ATTACH` y `DLL_THREAD_DETACH` casos en los `DllMain` función. Estos casos se pasan a `DllMain` cuando los subprocesos de adjuntar y separar desde el archivo DLL. Una llamada a [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc) cuando se está asociando un archivo DLL permite que la DLL mantener los índices de almacenamiento local (TLS) para cada subproceso asociado a la DLL del subproceso.

Tenga en cuenta que el archivo de encabezado Afxdllx.h contiene definiciones especiales para las estructuras utilizadas en archivos DLL de extensión MFC, como la definición de `AFX_EXTENSION_MODULE` y `CDynLinkLibrary`. Debe incluir este archivo de encabezado en el archivo DLL de extensión MFC.

> [!NOTE]
>  Es importante que no defina ni anular la definición de la `_AFX_NO_XXX` macros de Stdafx.h. Estas macros existen solo con el fin de comprobar si una plataforma de destino determinado admite esa característica o no. Puede escribir el programa para comprobar estas macros (por ejemplo, `#ifndef _AFX_NO_OLE_SUPPORT`), pero nunca en el programa debe definir o anular la definición de estas macros.

Una función de inicialización de ejemplo que se incluye identificadores de multithreading en [utilizando almacenamiento Local de subprocesos en una biblioteca de vínculos dinámicos](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library) en el SDK de Windows. Tenga en cuenta que el ejemplo contiene una función de punto de entrada denominada `LibMain`, pero debe dar nombre a esta función `DllMain` para que funcione con las bibliotecas de tiempo de ejecución de C y MFC.

## <a name="see-also"></a>Vea también

[Crear archivos DLL de C o C++ en Visual Studio](dlls-in-visual-cpp.md)<br/>
[Punto de entrada de DllMain](/windows/desktop/Dlls/dllmain)<br/>
[Procedimientos recomendados de la biblioteca de vínculos dinámicos](/windows/desktop/Dlls/dynamic-link-library-best-practices)

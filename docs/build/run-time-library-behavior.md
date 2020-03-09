---
title: Archivos dll y C++ comportamiento de la biblioteca en tiempo de ejecución visual
ms.date: 08/19/2019
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
ms.openlocfilehash: 572a0ba70c1ba2d46d2d9fd6d8ac543a77bbbc01
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856779"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Archivos dll y C++ comportamiento de la biblioteca en tiempo de ejecución visual

Al compilar una biblioteca de vínculos dinámicos (DLL) con Visual Studio, de forma predeterminada, el vinculador incluye C++ la biblioteca en tiempo de ejecución visual (VCRuntime). VCRuntime contiene el código necesario para inicializar y terminar un ejecutableC++ de C/. Cuando se vinculan a un archivo DLL, el código de VCRuntime proporciona una función de punto de entrada de DLL interna denominada `_DllMainCRTStartup` que controla los mensajes del sistema operativo Windows en el archivo DLL para asociar o Desasociar de un proceso o subproceso. La función `_DllMainCRTStartup` realiza tareas esenciales, como la configuración de la seguridad del búfer de pila, la inicialización y terminación de la biblioteca en tiempo de ejecución de C (CRT), y las llamadas a constructores y destructores para objetos estáticos y globales. `_DllMainCRTStartup` también llama a las funciones de enlace para otras bibliotecas como WinRT, MFC y ATL para realizar su propia inicialización y terminación. Sin esta inicialización, el CRT y otras bibliotecas, así como las variables estáticas, se dejarían en un estado no inicializado. Se llama a las mismas rutinas de inicialización y finalización internas de VCRuntime si el archivo DLL usa un CRT vinculado estáticamente o un archivo DLL de CRT vinculado dinámicamente.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Punto de entrada de DLL predeterminado _DllMainCRTStartup

En Windows, todos los archivos dll pueden contener una función de punto de entrada opcional, normalmente denominada `DllMain`, a la que se llama para la inicialización y la terminación. Esto le ofrece la oportunidad de asignar o liberar recursos adicionales según sea necesario. Windows llama a la función de punto de entrada en cuatro situaciones: Asociación de procesos, desasociación de procesos, Asociación de subprocesos y desasociación de subprocesos. Cuando se carga un archivo DLL en un espacio de direcciones de proceso, ya sea cuando se carga una aplicación que lo utiliza, o cuando la aplicación solicita el archivo DLL en tiempo de ejecución, el sistema operativo crea una copia independiente de los datos del archivo DLL. Esto se denomina *proceso de asociación*. La *Asociación de subprocesos* se produce cuando el proceso en el que se carga el archivo dll crea un nuevo subproceso. La *desasociación de subprocesos* se produce cuando finaliza el subproceso y la *desasociación de procesos* es cuando el archivo DLL ya no es necesario y se libera en una aplicación. El sistema operativo realiza una llamada independiente al punto de entrada de DLL para cada uno de estos eventos, pasando un argumento de *razón* para cada tipo de evento. Por ejemplo, el sistema operativo envía `DLL_PROCESS_ATTACH` como argumento de *motivo* para señalar el proceso de conexión.

La biblioteca VCRuntime proporciona una función de punto de entrada llamada `_DllMainCRTStartup` para administrar las operaciones predeterminadas de inicialización y finalización. Al adjuntar el proceso, la función `_DllMainCRTStartup` configura las comprobaciones de seguridad del búfer, inicializa CRT y otras bibliotecas, inicializa la información de tipo en tiempo de ejecución, inicializa y llama a los constructores para los datos estáticos y no locales, inicializa el almacenamiento local de subprocesos, incrementa un contador estático interno para cada asociación y, a continuación, llama a un `DllMain`proporcionado por el Al desasociar el proceso, la función pasa por estos pasos en orden inverso. Llama a `DllMain`, disminuye el contador interno, llama a destructores, llama a las funciones de terminación de CRT y a las funciones de `atexit` registradas, y notifica a cualquier otra biblioteca de terminación. Cuando el contador de datos adjuntos llega a cero, la función devuelve `FALSE` para indicar a Windows que se puede descargar el archivo DLL. También se llama a la función `_DllMainCRTStartup` durante la Asociación de subprocesos y la desasociación de subprocesos. En estos casos, el código de VCRuntime no realiza ninguna inicialización o terminación adicional y simplemente llama a `DllMain` para pasar el mensaje. Si `DllMain` devuelve `FALSE` de la Asociación de procesos, el error de señalización, `_DllMainCRTStartup` llama de nuevo a `DllMain` y pasa `DLL_PROCESS_DETACH` como argumento de *motivo* , pasa por el resto del proceso de finalización.

Al compilar archivos dll en Visual Studio, el punto de entrada predeterminado `_DllMainCRTStartup` proporcionado por VCRuntime se vincula automáticamente. No es necesario especificar una función de punto de entrada para el archivo DLL mediante la opción del enlazador [/entry (símbolo de punto de entrada)](reference/entry-entry-point-symbol.md) .

> [!NOTE]
> Aunque es posible especificar otra función de punto de entrada para un archivo DLL mediante la opción de vinculador/ENTRY:, no se recomienda, ya que la función de punto de entrada tendría que duplicar todo lo que `_DllMainCRTStartup` haga, en el mismo orden. VCRuntime proporciona funciones que permiten duplicar su comportamiento. Por ejemplo, puede llamar a [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) inmediatamente en el proceso de adjuntar para admitir la opción de comprobación de búfer [/GS (comprobación de seguridad del búfer)](reference/gs-buffer-security-check.md) . Puede llamar a la función `_CRT_INIT`, pasando los mismos parámetros que la función de punto de entrada, para realizar el resto de las funciones de inicialización o finalización de DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicializar un archivo DLL

Es posible que el archivo DLL tenga código de inicialización que deba ejecutarse cuando se cargue el archivo DLL. Para poder realizar sus propias funciones de inicialización y finalización de DLL, `_DllMainCRTStartup` llama a una función llamada `DllMain` que puede proporcionar. El `DllMain` debe tener la firma necesaria para un punto de entrada de DLL. La función de punto de entrada predeterminada `_DllMainCRTStartup` llama a `DllMain` utilizando los mismos parámetros pasados por Windows. De forma predeterminada, si no se proporciona una función de `DllMain`, Visual Studio proporciona una para usted y la vincula para que `_DllMainCRTStartup` siempre tenga algo que llamar. Esto significa que, si no es necesario inicializar el archivo DLL, no es necesario hacer nada especial al compilar el archivo DLL.

Esta es la firma utilizada para `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Algunas bibliotecas ajustan la función de `DllMain`. Por ejemplo, en un archivo DLL de MFC normal, implemente las funciones miembro `InitInstance` y `ExitInstance` del objeto `CWinApp` para realizar la inicialización y la terminación que requiere el archivo DLL. Para obtener más información, vea la sección [inicializar archivos dll de MFC normales](#initializing-regular-dlls) .

> [!WARNING]
> Hay límites importantes sobre lo que puede hacer con seguridad en un punto de entrada de DLL. Consulte las [prácticas recomendadas generales](/windows/win32/Dlls/dynamic-link-library-best-practices) para las API de Windows específicas que no se pueden llamar en `DllMain`. Si necesita algo, pero la inicialización más sencilla lo hace en una función de inicialización para el archivo DLL. Puede requerir que las aplicaciones llamen a la función de inicialización después de que se haya ejecutado `DllMain` y antes de llamar a otras funciones del archivo DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializar archivos dll normales (no MFC)

Para realizar su propia inicialización en archivos dll normales (no MFC) que usan el punto de entrada `_DllMainCRTStartup` proporcionado por VCRuntime, el código fuente del archivo DLL debe contener una función llamada `DllMain`. En el código siguiente se presenta un esqueleto básico en el que se muestra el aspecto de la definición de `DllMain`:

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
> La documentación de Windows SDK anterior indica que el nombre real de la función de punto de entrada de DLL debe especificarse en la línea de comandos del vinculador con la opción/ENTRY. Con Visual Studio, no es necesario usar la opción/ENTRY si el nombre de la función de punto de entrada es `DllMain`. De hecho, si usa la opción/ENTRY y asigna un nombre a la función de punto de entrada que no sea `DllMain`, CRT no se inicializa correctamente a menos que la función de punto de entrada realice las mismas llamadas de inicialización que `_DllMainCRTStartup` realiza.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicializar archivos dll de MFC normales

Dado que los archivos dll normales de MFC tienen un objeto `CWinApp`, deben realizar sus tareas de inicialización y finalización en la misma ubicación que una aplicación MFC: en las funciones miembro `InitInstance` y `ExitInstance` de la clase derivada `CWinApp`del archivo DLL. Dado que MFC proporciona una función `DllMain` a la que llama `_DllMainCRTStartup` para `DLL_PROCESS_ATTACH` y `DLL_PROCESS_DETACH`, no debe escribir su propia función `DllMain`. La función `DllMain` proporcionada por MFC llama `InitInstance` cuando se carga el archivo DLL y llama a `ExitInstance` antes de que se descargue el archivo DLL.

Un archivo DLL de MFC normal puede realizar un seguimiento de varios subprocesos llamando a [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) y [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) en su función `InitInstance`. Estas funciones permiten que el archivo DLL realice un seguimiento de los datos específicos del subproceso.

En el archivo DLL de MFC normal que se vincula dinámicamente a MFC, si utiliza cualquier MFC OLE, base de datos MFC (o DAO) o compatibilidad con sockets MFC, respectivamente, los archivos dll de la extensión MFC MFCO*versión*d. dll, MFCD*versión*d. dll y MFCN*versión*d. dll (donde *versión* es el número de versión) se vinculan de forma automática. Debe llamar a una de las siguientes funciones de inicialización predefinidas para cada uno de estos archivos DLL que use en la `CWinApp::InitInstance`de la DLL de MFC normal.

|Tipo de compatibilidad con MFC|Función de inicialización a la que se llama|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*versión*D. dll)|`AfxOleInitModule`|
|Base de datos MFC (MFCD*versión*D. dll)|`AfxDbInitModule`|
|Sockets MFC (*versión*D. dll de MFCN)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicializar archivos dll de extensión MFC

Dado que los archivos dll de extensión de MFC no tienen un objeto derivado de `CWinApp`(como los archivos dll normales de MFC), debe agregar el código de inicialización y finalización a la función `DllMain` que genera el Asistente para archivos DLL de MFC.

El asistente proporciona el código siguiente para los archivos dll de extensión de MFC. En el código, `PROJNAME` es un marcador de posición para el nombre del proyecto.

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
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

La creación de un nuevo `CDynLinkLibrary` objeto durante la inicialización permite que el archivo DLL de extensión de MFC exporte `CRuntimeClass` objetos o recursos a la aplicación cliente.

Si va a utilizar el archivo DLL de extensión de MFC desde uno o varios archivos dll normales de MFC, debe exportar una función de inicialización que cree un objeto de `CDynLinkLibrary`. Se debe llamar a esa función desde cada uno de los archivos dll de MFC estándar que utilizan el archivo DLL de extensión de MFC. Un lugar adecuado para llamar a esta función de inicialización es en la `InitInstance` función miembro del objeto derivado `CWinApp`del archivo DLL de MFC normal antes de usar cualquiera de las clases o funciones exportadas del archivo DLL de extensión de MFC.

En el `DllMain` que genera el Asistente para archivos DLL de MFC, la llamada a `AfxInitExtensionModule` captura las clases de tiempo de ejecución del módulo (estructuras`CRuntimeClass`), así como sus generadores de objetos (objetos`COleObjectFactory`) para su uso cuando se crea el objeto `CDynLinkLibrary`. Debe comprobar el valor devuelto de `AfxInitExtensionModule`; Si `AfxInitExtensionModule`devuelve un valor cero, devuelva cero desde la función `DllMain`.

Si el archivo DLL de extensión de MFC va a vincularse explícitamente a un archivo ejecutable (lo que significa que el ejecutable llama `AfxLoadLibrary` para vincular al archivo DLL), debe agregar una llamada a `AfxTermExtensionModule` en `DLL_PROCESS_DETACH`. Esta función permite que MFC Limpie el archivo DLL de extensión de MFC cuando cada proceso se desasocie del archivo DLL de extensión de MFC (lo que sucede cuando el proceso finaliza o cuando se descarga el archivo DLL como resultado de una llamada `AfxFreeLibrary`). Si el archivo DLL de extensión de MFC se vinculará implícitamente a la aplicación, no es necesario realizar la llamada a `AfxTermExtensionModule`.

Las aplicaciones que se vinculan explícitamente a los archivos dll de extensión de MFC deben llamar a `AfxTermExtensionModule` al liberar la DLL. También deben usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de las funciones de Win32 `LoadLibrary` y `FreeLibrary`) si la aplicación usa varios subprocesos. El uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión de MFC no daña el estado global de MFC.

Dado que MFCx0. dll se inicializa por completo en el momento en que se llama a `DllMain`, puede asignar memoria y llamar a funciones de MFC en `DllMain` (a diferencia de la versión de 16 bits de MFC).

Los archivos dll de extensión pueden encargarse del multithreading mediante el control de los casos de `DLL_THREAD_ATTACH` y `DLL_THREAD_DETACH` en la función `DllMain`. Estos casos se pasan a `DllMain` cuando los subprocesos se asocian y desasocian de la DLL. La llamada a [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) cuando se asocia un archivo DLL permite que el archivo dll mantenga índices de almacenamiento local de subprocesos (TLS) para cada subproceso asociado a la dll.

Tenga en cuenta que el archivo de encabezado AFXDLLX. h contiene definiciones especiales para estructuras utilizadas en archivos dll de extensión de MFC, como la definición de `AFX_EXTENSION_MODULE` y `CDynLinkLibrary`. Debe incluir este archivo de encabezado en la DLL de extensión de MFC.

> [!NOTE]
>  Es importante no definir ni anular la definición de ninguna de las macros `_AFX_NO_XXX` en *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores). Estas macros solo existen con el fin de comprobar si una plataforma de destino concreta admite esa característica o no. Puede escribir el programa para comprobar estas macros (por ejemplo, `#ifndef _AFX_NO_OLE_SUPPORT`), pero el programa nunca debe definir o anular la definición de estas macros.

Una función de inicialización de ejemplo que controla el multithreading se incluye en el [uso de almacenamiento local de subprocesos en una biblioteca de vínculos dinámicos](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) en el Windows SDK. Tenga en cuenta que el ejemplo contiene una función de punto de entrada denominada `LibMain`, pero debe asignar un nombre a esta función `DllMain` para que funcione con las bibliotecas en tiempo de ejecución de MFC y C.

## <a name="see-also"></a>Consulte también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)<br/>
[Punto de entrada de DllMain](/windows/win32/Dlls/dllmain)<br/>
[Procedimientos recomendados de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-best-practices)

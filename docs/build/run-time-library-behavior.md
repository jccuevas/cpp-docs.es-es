---
title: Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++
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
ms.openlocfilehash: 2f2ffb13e6a80b144298bbf8cd76b5666a10b4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335665"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++

Al compilar una biblioteca de vínculos dinámicos (DLL) mediante Visual Studio, de forma predeterminada, el vinculador incluye la biblioteca en tiempo de ejecución de Visual C++ (VCRuntime). VCRuntime contiene el código necesario para inicializar y terminar un ejecutable de C/C++. Cuando se vincula a un archivo DLL, el código `_DllMainCRTStartup` VCRuntime proporciona una función de punto de entrada DLL interna llamada que controla los mensajes del sistema operativo Windows al archivo DLL para adjuntar o separar de un proceso o subproceso. La `_DllMainCRTStartup` función realiza tareas esenciales como la configuración de seguridad de búfer de pila, la inicialización y terminación de la biblioteca en tiempo de ejecución de C (CRT) y las llamadas a constructores y destructores para objetos estáticos y globales. `_DllMainCRTStartup`también llama a funciones de enlace para otras bibliotecas como WinRT, MFC y ATL para realizar su propia inicialización y terminación. Sin esta inicialización, el CRT y otras bibliotecas, así como las variables estáticas, se dejarían en un estado no inicializado. Las mismas rutinas de inicialización y terminación internas de VCRuntime se llaman si el archivo DLL utiliza un CRT vinculado estáticamente o un archivo DLL de CRT vinculado dinámicamente.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Punto de entrada DLL predeterminado _DllMainCRTStartup

En Windows, todos los archivos DLL pueden contener una `DllMain`función de punto de entrada opcional, normalmente llamada , que se llama para la inicialización y la terminación. Esto le da la oportunidad de asignar o liberar recursos adicionales según sea necesario. Windows llama a la función de punto de entrada en cuatro situaciones: conexión de proceso, desasociación de proceso, conexión de subprocesos y desasociación de subprocesos. Cuando se carga un archivo DLL en un espacio de direcciones de proceso, ya sea cuando se carga una aplicación que lo utiliza o cuando la aplicación solicita el archivo DLL en tiempo de ejecución, el sistema operativo crea una copia independiente de los datos DLL. Esto se denomina *proceso adjunto*. *La conexión* de subprocesos se produce cuando el proceso en el que se carga el archivo DLL crea un nuevo subproceso. *La desasociación* de subprocesos se produce cuando finaliza el subproceso y la *desasociación* del proceso es cuando el archivo DLL ya no es necesario y es liberado por una aplicación. El sistema operativo realiza una llamada independiente al punto de entrada DLL para cada uno de estos eventos, pasando un argumento *de motivo* para cada tipo de evento. Por ejemplo, el `DLL_PROCESS_ATTACH` sistema operativo envía como argumento *de razón* para señalar el proceso adjunto.

La biblioteca VCRuntime proporciona una `_DllMainCRTStartup` función de punto de entrada llamada para controlar las operaciones de inicialización y terminación predeterminadas. En la asociación de procesos, la `_DllMainCRTStartup` función configura comprobaciones de seguridad de búfer, inicializa el CRT y otras bibliotecas, inicializa la información de tipo en tiempo de ejecución, inicializa y llama a `DllMain`constructores para datos estáticos y no locales, inicializa el almacenamiento local de subprocesos, incrementa un contador estático interno para cada adjunto y, a continuación, llama a un usuario o biblioteca proporcionado. Al separar el proceso, la función pasa por estos pasos en sentido inverso. Llama `DllMain`, disminuye el contador interno, llama a destructores, `atexit` llama a funciones de terminación de CRT y funciones registradas, y notifica a cualquier otra biblioteca de terminación. Cuando el contador de datos adjuntos va a cero, la función vuelve `FALSE` a indicar a Windows que se puede descargar el archivo DLL. También `_DllMainCRTStartup` se llama a la función durante la conexión de subprocesos y la desasociación de subprocesos. En estos casos, el código VCRuntime no realiza ninguna inicialización o terminación adicional por sí solo, y solo llama `DllMain` para pasar el mensaje. Si `DllMain` `FALSE` vuelve del proceso `_DllMainCRTStartup` adjunta, el error de señalización, las llamadas `DllMain` otra vez y pasa `DLL_PROCESS_DETACH` como argumento de la *razón,* después pasa a través del resto del proceso de terminación.

Al compilar archivos DLL en Visual Studio, el punto `_DllMainCRTStartup` de entrada predeterminado proporcionado por VCRuntime se vincula automáticamente. No es necesario especificar una función de punto de entrada para el archivo DLL mediante la opción del vinculador [/ENTRY (símbolo](reference/entry-entry-point-symbol.md) de punto de entrada).

> [!NOTE]
> Aunque es posible especificar otra función de punto de entrada para un archivo DLL mediante la opción del vinculador /ENTRY:, no se recomienda, porque la función de punto de entrada tendría que duplicar todo lo que `_DllMainCRTStartup` lo hace, en el mismo orden. VCRuntime proporciona funciones que le permiten duplicar su comportamiento. Por ejemplo, puede llamar a [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) inmediatamente en la conexión de proceso para admitir la opción de comprobación de búfer [/GS (comprobación](reference/gs-buffer-security-check.md) de seguridad de búfer). Puede llamar `_CRT_INIT` a la función, pasando los mismos parámetros que la función de punto de entrada, para realizar el resto de las funciones de inicialización o terminación de DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicializar un archivo DLL

El archivo DLL puede tener código de inicialización que debe ejecutarse cuando se carga el archivo DLL. Para que pueda realizar sus propias funciones de inicialización y terminación de DLL, `_DllMainCRTStartup` llama a una función llamada `DllMain` que puede proporcionar. Debe `DllMain` tener la firma necesaria para un punto de entrada DLL. La función `_DllMainCRTStartup` de `DllMain` punto de entrada predeterminada llama utilizando los mismos parámetros pasados por Windows. De forma predeterminada, si `DllMain` no proporciona una función, Visual Studio `_DllMainCRTStartup` proporciona una para usted y la vincula para que siempre tenga algo que llamar. Esto significa que si no necesita inicializar el archivo DLL, no hay nada especial que tenga que hacer al compilar el archivo DLL.

Esta es la `DllMain`firma utilizada para:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Algunas bibliotecas `DllMain` ajustan la función por usted. Por ejemplo, en un archivo `CWinApp` DLL de `InitInstance` `ExitInstance` MFC normal, implemente las funciones miembro y del objeto para realizar la inicialización y terminación requeridas por el archivo DLL. Para obtener más información, vea la sección [Inicializar archivos DLL de MFC normales.](#initializing-regular-dlls)

> [!WARNING]
> Hay límites significativos en lo que puede hacer de forma segura en un punto de entrada de DLL. Consulte [Procedimientos recomendados](/windows/win32/Dlls/dynamic-link-library-best-practices) generales para las API `DllMain`de Windows específicas que no son seguras para llamar. Si necesita algo que no sea la inicialización más simple, hála en una función de inicialización para el archivo DLL. Puede requerir que las aplicaciones `DllMain` llamen a la función de inicialización después de que se haya ejecutado y antes de que llamen a cualquier otra función del archivo DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializar archivos DLL ordinarios (no MFC)

Para realizar su propia inicialización en archivos DLL normales (no `_DllMainCRTStartup` MFC) que utilizan el punto `DllMain`de entrada proporcionado por VCRuntime, el código fuente DLL debe contener una función denominada . El código siguiente presenta un esqueleto `DllMain` básico que muestra cómo podría ser la definición de:

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
> La documentación anterior del SDK de Windows indica que el nombre real de la función de punto de entrada DLL debe especificarse en la línea de comandos del vinculador con la opción /ENTRY. Con Visual Studio, no es necesario usar la opción /ENTRY si `DllMain`el nombre de la función de punto de entrada es . De hecho, si utiliza la opción /ENTRY y asigna `DllMain`un nombre a la función de punto de entrada que `_DllMainCRTStartup` no sea , el CRT no se inicializa correctamente a menos que la función de punto de entrada realice las mismas llamadas de inicialización que realiza.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicializar archivos DLL de MFC normales

Dado que los archivos `CWinApp` DLL de MFC normales tienen un objeto, deben realizar sus `InitInstance` `ExitInstance` tareas de inicialización `CWinApp`y finalización en la misma ubicación que una aplicación MFC: en las funciones y miembros de la clase derivada del archivo DLL. Dado que `DllMain` MFC proporciona una `_DllMainCRTStartup` `DLL_PROCESS_ATTACH` función a la que llama for y `DLL_PROCESS_DETACH`, no debe escribir su propia `DllMain` función. La función `DllMain` proporcionada `InitInstance` por MFC llama cuando `ExitInstance` se carga el archivo DLL y llama antes de descargar el archivo DLL.

Un archivo DLL de MFC normal puede realizar un seguimiento de `InitInstance` varios subprocesos mediante una llamada a [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) y [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) en su función. Estas funciones permiten al archivo DLL realizar un seguimiento de los datos específicos del subproceso.

En el archivo DLL de MFC normal que se vincula dinámicamente a MFC, si usa cualquier COMPATIBILIDAD con MFC OLE, MFC Database (o DAO) o MFC Sockets, respectivamente, los archivos DLL de extensión MFCMFCO*versión*D.dll, MFCD*versión*D.dll y MFCN*versión*D.dll (donde *la versión* es el número de versión) se vinculan automáticamente. Debe llamar a una de las siguientes funciones de inicialización predefinidas para cada `CWinApp::InitInstance`uno de estos archivos DLL que está utilizando en el archivo DLL de MFC normal.

|Tipo de compatibilidad con MFC|Función de inicialización para llamar|
|-------------------------|-------------------------------------|
|MFC OLE *(versión*DeCMO D.dll)|`AfxOleInitModule`|
|Base de datos MFC *(versión*MFCD D.dll)|`AfxDbInitModule`|
|Sockets MFC *(versión*D.dll de MFCN)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicializar archivos DLL de extensión MFC

Dado que los archivos DLL `CWinApp`de extensión MFC no tienen un objeto derivado (al igual que `DllMain` los archivos DLL de MFC normales), debe agregar el código de inicialización y terminación a la función que genera el Asistente para DLL de MFC.

El asistente proporciona el código siguiente para los archivos DLL de extensión MFC. En el `PROJNAME` código, es un marcador de posición para el nombre del proyecto.

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

La creación `CDynLinkLibrary` de un nuevo objeto durante `CRuntimeClass` la inicialización permite que el archivo DLL de extensión MFC exporte objetos o recursos a la aplicación cliente.

Si va a usar el archivo DLL de extensión MFC desde uno o varios archivos `CDynLinkLibrary` DLL de MFC normales, debe exportar una función de inicialización que cree un objeto. Esa función debe llamarse desde cada uno de los archivos DLL de MFC normales que usan el archivo DLL de extensión MFC. Un lugar adecuado para llamar a `InitInstance` esta función de inicialización está en la función miembro del objeto derivado de `CWinApp`DLL de MFC normal antes de usar cualquiera de las clases o funciones exportadas del archivo DLL de extensión MFC.

En `DllMain` el que genera el Asistente `AfxInitExtensionModule` para DLL de MFC, la`CRuntimeClass` llamada para capturar las clases`COleObjectFactory` en tiempo de `CDynLinkLibrary` ejecución del módulo (estructuras) así como sus generadores de objetos ( objetos) para su uso cuando se crea el objeto. Debe comprobar el valor `AfxInitExtensionModule`devuelto de ; si se devuelve un `AfxInitExtensionModule`valor cero `DllMain` desde , devuelve cero de la función.

Si el archivo DLL de extensión MFC se vinculará `AfxLoadLibrary` explícitamente a un archivo ejecutable `AfxTermExtensionModule` (es decir, el archivo ejecutable llama a vincular al archivo DLL), debe agregar una llamada a on `DLL_PROCESS_DETACH`. Esta función permite a MFC limpiar el archivo DLL de extensión MFC cuando cada proceso se separa del archivo DLL `AfxFreeLibrary` de extensión MFC (lo que ocurre cuando se cierra el proceso o cuando se descarga el archivo DLL como resultado de una llamada). Si el archivo DLL de extensión MFC se vinculará implícitamente a la aplicación, la llamada a `AfxTermExtensionModule` no es necesaria.

Las aplicaciones que se vinculan explícitamente `AfxTermExtensionModule` a archivos DLL de extensión MFC deben llamar al liberar el archivo DLL. También deben `AfxLoadLibrary` usar `AfxFreeLibrary` y (en lugar `LoadLibrary` de `FreeLibrary`las funciones Win32 y ) si la aplicación utiliza varios subprocesos. Usar `AfxLoadLibrary` `AfxFreeLibrary` y garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión MFC no daña el estado global de MFC.

Dado que el MFCx0.dll se `DllMain` inicializa completamente por el tiempo se `DllMain` llama, puede asignar memoria y llamar a funciones MFC dentro (a diferencia de la versión de 16 bits de MFC).

Los archivos DLL de extensión pueden encargarse del multithreading controlando los `DLL_THREAD_ATTACH` casos y los `DLL_THREAD_DETACH` de la `DllMain` función. Estos casos se `DllMain` pasan cuando los subprocesos se adjuntan y se desasocian del archivo DLL. Llamar a [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) cuando se adjunta un archivo DLL permite que el archivo DLL mantenga índices de almacenamiento local de subprocesos (TLS) para cada subproceso asociado al archivo DLL.

Tenga en cuenta que el archivo de encabezado Afxdllx.h contiene definiciones especiales para `AFX_EXTENSION_MODULE` `CDynLinkLibrary`las estructuras utilizadas en los archivos DLL de extensión MFC, como la definición para y . Debe incluir este archivo de encabezado en el archivo DLL de extensión MFC.

> [!NOTE]
> Es importante que no defina ni desactive `_AFX_NO_XXX` ninguna de las macros de *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores). Estas macros existen solo con el fin de comprobar si una plataforma de destino determinada admite esa característica o no. Puede escribir el programa para comprobar estas `#ifndef _AFX_NO_OLE_SUPPORT`macros (por ejemplo, ), pero el programa nunca debe definir o anular la definición de estas macros.

Una función de inicialización de ejemplo que controla el multithreading se incluye en Uso del almacenamiento local de [subprocesos en una biblioteca de vínculos dinámicos](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) en el Windows SDK. Tenga en cuenta que el ejemplo `LibMain`contiene una función `DllMain` de punto de entrada llamada , pero debe asignar un nombre a esta función para que funcione con las bibliotecas en tiempo de ejecución MFC y C.

## <a name="see-also"></a>Consulte también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)<br/>
[Punto de entrada DllMain](/windows/win32/Dlls/dllmain)<br/>
[Prácticas recomendadas de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-best-practices)

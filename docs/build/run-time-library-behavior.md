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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335665"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++

Al compilar una biblioteca de vínculos dinámicos (DLL) con Visual Studio, de forma predeterminada, el enlazador la biblioteca en tiempo de ejecución de Visual C++ (VCRuntime). VCRuntime contiene el código necesario para inicializar y finalizar un ejecutable de C/C++. Cuando se vincula a un archivo DLL, el código de VCRuntime proporciona una función de punto de entrada de DLL interna denominada `_DllMainCRTStartup` que controla los mensajes del sistema operativo Windows en el archivo DLL para asociar o desasociar de un proceso o subproceso. La función `_DllMainCRTStartup` realiza tareas esenciales, como la configuración de la seguridad del búfer de pila, la inicialización y finalización de la biblioteca en tiempo de ejecución de C (CRT), y las llamadas a constructores y destructores para objetos estáticos y globales. `_DllMainCRTStartup` también llama a las funciones de enlace para que otras bibliotecas como WinRT, MFC y ATL realicen su propia inicialización y finalización. Sin esta inicialización, CRT y otras bibliotecas, así como las variables estáticas, se dejarían en un estado no inicializado. Se llama a las mismas rutinas de inicialización y finalización internas de VCRuntime, con independencia de si el archivo DLL usa un CRT vinculado de forma estática o un archivo DLL de CRT vinculado de forma dinámica.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Punto de entrada de DLL predeterminado _DllMainCRTStartup

En Windows, todos los archivos DLL pueden contener una función de punto de entrada opcional, normalmente denominada `DllMain`, a la que se llama para la inicialización y la finalización. Esto permite asignar o liberar recursos adicionales según sea necesario. Windows llama a la función de punto de entrada en cuatro situaciones: asociación de procesos, desasociación de procesos, asociación de subprocesos y desasociación de subprocesos. Cuando se carga un archivo DLL en un espacio de direcciones de proceso, ya sea cuando se carga una aplicación que lo usa, o bien cuando la aplicación solicita el archivo DLL en tiempo de ejecución, el sistema operativo crea una copia independiente de los datos del archivo DLL. Esto se denomina *asociación de procesos*. La *asociación de subprocesos* se produce cuando el proceso en el que se carga el archivo DLL crea un subproceso. La *desasociación de subprocesos* se produce cuando finaliza el subproceso y la *desasociación del proceso*, cuando el archivo DLL ya no es necesario y se libera en una aplicación. El sistema operativo realiza una llamada independiente al punto de entrada de DLL para cada uno de estos eventos, y pasa un argumento de *motivo* para cada tipo de evento. Por ejemplo, el sistema operativo envía `DLL_PROCESS_ATTACH` como argumento de *motivo* para indicar la asociación de procesos.

La biblioteca VCRuntime proporciona una función de punto de entrada llamada `_DllMainCRTStartup` para administrar las operaciones predeterminadas de inicialización y finalización. Al asociar el proceso, la función `_DllMainCRTStartup` configura las comprobaciones de seguridad del búfer, inicializa CRT y otras bibliotecas, inicializa la información de tipos en tiempo de ejecución, inicializa y llama a constructores para datos estáticos y no locales, inicializa el almacenamiento local de subprocesos, incrementa un contador estático interno para cada asociación y, después, llama a un elemento `DllMain`proporcionado por la biblioteca o el usuario. Al desasociar el proceso, la función realiza estos pasos en orden inverso. Llama a `DllMain`, disminuye el contador interno, llama a destructores, a las funciones de finalización de CRT y a las funciones de `atexit` registradas, y notifica la finalización a cualquier otra biblioteca. Cuando el contador de datos adjuntos llega a cero, la función devuelve `FALSE` para indicar a Windows que el archivo DLL se puede descargar. También se llama a la función `_DllMainCRTStartup` durante la asociación y la desasociación de subprocesos. En estos casos, el código de VCRuntime no realiza ninguna inicialización o finalización adicional, y simplemente llama a `DllMain` para pasar el mensaje. Si `DllMain` devuelve `FALSE` de la asociación de procesos, para indicar un error, `_DllMainCRTStartup` llama de nuevo a `DllMain` y pasa `DLL_PROCESS_DETACH` como argumento de *motivo*, para después pasar por el resto del proceso de finalización.

Al compilar archivos DLL en Visual Studio, el punto de entrada predeterminado `_DllMainCRTStartup` proporcionado por VCRuntime se vincula de forma automática. No es necesario especificar ninguna función de punto de entrada para el archivo DLL mediante la opción del enlazador [/ENTRY (símbolo de punto de entrada)](reference/entry-entry-point-symbol.md).

> [!NOTE]
> Aunque es posible especificar otra función de punto de entrada para un archivo DLL mediante la opción del enlazador /ENTRY:, no es recomendable porque la función de punto de entrada tendría que duplicar todo lo que hace `_DllMainCRTStartup`, en el mismo orden. VCRuntime proporciona funciones que permiten duplicar su comportamiento. Por ejemplo, puede llamar a [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) inmediatamente durante la asociación del proceso para admitir la opción de comprobación del búfer [/GS (comprobación de seguridad del búfer)](reference/gs-buffer-security-check.md). Puede llamar a la función `_CRT_INIT` y pasar los mismos parámetros de la función de punto de entrada, para realizar el resto de las funciones de inicialización o finalización de DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicializar un archivo DLL

Es posible que en el archivo DLL haya código de inicialización que se tenga que ejecutar cuando se cargue el archivo DLL. Para poder realizar funciones de inicialización y finalización de DLL propias, `_DllMainCRTStartup` llama a una función denominada `DllMain` que puede proporcionar. `DllMain` debe tener la firma necesaria para un punto de entrada de DLL. La función de punto de entrada predeterminada `_DllMainCRTStartup` llama a `DllMain` con los mismos parámetros pasados por Windows. De forma predeterminada, si no proporciona ninguna función `DllMain`, Visual Studio proporciona una de forma automática y la vincula para que `_DllMainCRTStartup` siempre tenga algo a lo que llamar. Esto significa que, si no necesita inicializar el archivo DLL, no tendrá que hacer nada especial cuando lo compile.

Esta es la firma que se usa para `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Algunas bibliotecas encapsulan la función `DllMain` de forma automática. Por ejemplo, en un archivo DLL de MFC estándar, implemente las funciones miembro `InitInstance` y `ExitInstance` del objeto `CWinApp` para realizar la inicialización y la finalización que requiere el archivo DLL. Para obtener más información, vea la sección [Inicialización de archivos DLL estándar de MFC](#initializing-regular-dlls).

> [!WARNING]
> Hay límites importantes sobre lo que se puede hacer de forma segura en un punto de entrada del archivo DLL. Vea [Procedimientos recomendados generales](/windows/win32/Dlls/dynamic-link-library-best-practices) para API de Windows concretas que no son seguras para llamar en `DllMain`. Si necesita algo más que la inicialización más sencilla, puede hacerlo en una función de inicialización para el archivo DLL. Puede requerir que las aplicaciones llamen a la función de inicialización después de que se haya ejecutado `DllMain` y antes de llamar a otras funciones del archivo DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicialización de DLL estándar (no basadas en MFC)

Para realizar la inicialización propia en DLL estándar (no basadas en MFC) que usan el punto de entrada `_DllMainCRTStartup` proporcionado por VCRuntime, el código fuente de la DLL debe contener una función llamada `DllMain`. En el código siguiente se presenta una estructura básica en la que se muestra el aspecto de la definición de `DllMain`:

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
> En la documentación de Windows SDK anterior se afirma que el nombre real de la función de punto de entrada del archivo DLL se debe especificar en la línea de comandos del enlazador con la opción /ENTRY. Con Visual Studio, no es necesario usar la opción /ENTRY si el nombre de la función de punto de entrada es `DllMain`. De hecho, si usa la opción /ENTRY y asigna un nombre a la función de punto de entrada que no sea `DllMain`, CRT no se inicializa correctamente a menos que la función de punto de entrada realice las mismas llamadas de inicialización que `_DllMainCRTStartup`.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicialización de archivos DLL de MFC estándar

Como los archivos DLL de MFC estándar tienen un objeto `CWinApp`, deben realizar sus tareas de inicialización y finalización en la misma ubicación que una aplicación MFC: en las funciones miembro `InitInstance` y `ExitInstance` de la clase derivada de `CWinApp` de la DLL. Como MFC proporciona una función `DllMain` a la que `_DllMainCRTStartup` llama para `DLL_PROCESS_ATTACH` y `DLL_PROCESS_DETACH`, no debe escribir una función `DllMain` propia. La función `DllMain` proporcionada por MFC llama a `InitInstance` cuando se carga la DLL y a `ExitInstance` antes de que se descargue.

Un archivo DLL de MFC estándar puede realizar el seguimiento de varios subprocesos mediante la llamada a [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) y [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) en su función `InitInstance`. Estas funciones permiten que la DLL realice el seguimiento de datos específicos del subproceso.

En la DLL de MFC estándar que se vincula de forma dinámica a MFC, si usa cualquier compatibilidad con OLE de MFC, base de datos MFC (o DAO) o sockets MFC, respectivamente, los archivos DLL de extensión MFC de depuración de MFC MFCO*versión*D.dll, MFCD*versión*D.dll y MFCN*versión*D.dll (donde *versión* es el número de versión) se vinculan automáticamente. Debe llamar a una de las siguientes funciones de inicialización predefinidas para cada una de estas DLL que use en `CWinApp::InitInstance` de la DLL de MFC estándar.

|Tipo de compatibilidad con MFC|Función de inicialización a la que se llama|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*versión*D.dll)|`AfxOleInitModule`|
|Base de datos de MFC (MFCD*versión*D.dll)|`AfxDbInitModule`|
|Sockets de MFC (MFCN*versión*D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicialización de archivos DLL de extensión MFC

Como los archivos DLL de extensión MFC no tienen un objeto derivado de `CWinApp`(como las DLL de MFC estándar), debe agregar el código de inicialización y finalización a la función `DllMain` que genera el Asistente para archivos DLL de MFC.

El asistente proporciona el código siguiente para los archivos DLL de extensión de MFC. En el código, `PROJNAME` es un marcador de posición para el nombre del proyecto.

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

La creación de un objeto `CDynLinkLibrary` durante la inicialización permite al archivo DLL de extensión de MFC exportar objetos `CRuntimeClass` o recursos a la aplicación cliente.

Si va a usar el archivo DLL de extensión de MFC desde uno o varios archivos DLL de MFC estándar, tendrá que exportar una función de inicialización que cree un objeto `CDynLinkLibrary`. Se debe llamar a esa función desde cada uno de los archivos DLL de MFC estándar que usan el archivo DLL de extensión de MFC. Un lugar adecuado para llamar a esta función de inicialización es la función miembro `InitInstance` del objeto derivado de `CWinApp` del archivo DLL de MFC estándar antes de usar cualquiera de las clases o funciones exportadas del archivo DLL de extensión de MFC.

En el elemento `DllMain` que genera el Asistente para archivos DLL de MFC, la llamada a `AfxInitExtensionModule` captura las clases de tiempo de ejecución del módulo (estructuras `CRuntimeClass`), así como sus generadores de objetos (objetos `COleObjectFactory`) para su uso cuando se crea el objeto `CDynLinkLibrary`. Debe comprobar el valor devuelto de `AfxInitExtensionModule`; si `AfxInitExtensionModule` devuelve un valor cero, devuelva cero desde la función `DllMain`.

Si el archivo DLL de extensión de MFC se va a vincular de forma explícita a un archivo ejecutable (lo que significa que el ejecutable llama a `AfxLoadLibrary` para vincular al archivo DLL), debe agregar una llamada a `AfxTermExtensionModule` en `DLL_PROCESS_DETACH`. Esta función permite que MFC limpie el archivo DLL de extensión de MFC cuando cada proceso se desasocie del archivo DLL de extensión de MFC (lo que sucede cuando el proceso finaliza o cuando el archivo DLL se descarga como resultado de una llamada a `AfxFreeLibrary`). Si el archivo DLL de extensión de MFC se va a vincular de forma implícita a la aplicación, no es necesario realizar la llamada a `AfxTermExtensionModule`.

Las aplicaciones que se vinculan de forma explícita a archivos DLL de extensión de MFC deben llamar a `AfxTermExtensionModule` al liberar la DLL. También deben usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de las funciones `LoadLibrary` y `FreeLibrary` de Win32) si la aplicación usa varios subprocesos. El uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión de MFC no daña el estado global de MFC.

Como MFCx0.dll se inicializa por completo cuando se llama a `DllMain`, puede asignar memoria y llamar a funciones de MFC en `DllMain` (a diferencia de la versión de MFC de 16 bits).

Los archivos DLL de extensión se pueden encargar del multithreading mediante el control de los casos de `DLL_THREAD_ATTACH` y `DLL_THREAD_DETACH` en la función `DllMain`. Estos casos se pasan a `DllMain` cuando los subprocesos se asocian y desasocian de la DLL. Llamar a [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) cuando se asocia un archivo DLL permite que el archivo DLL mantenga índices de almacenamiento local para el subproceso (TLS) para cada subproceso asociado a la DLL.

Tenga en cuenta que el archivo de encabezado Afxdllx.h contiene definiciones especiales para estructuras que se usan en archivos DLL de extensión de MFC, como la definición de `AFX_EXTENSION_MODULE` y `CDynLinkLibrary`. Debe incluir este archivo de encabezado en la DLL de extensión de MFC.

> [!NOTE]
> Es importante no definir ni anular la definición de ninguna de las macros `_AFX_NO_XXX` en *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores). Estas macros solo existen para comprobar si una plataforma de destino concreta admite esa característica o no. Puede escribir el programa para que compruebe estas macros (por ejemplo, `#ifndef _AFX_NO_OLE_SUPPORT`), pero nunca debe definirlas ni anular su definición.

En Windows SDK, en [Uso de almacenamiento local para el subproceso en una biblioteca de vínculos dinámicos](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library), se incluye una función de inicialización de ejemplo que controla el multithreading. Tenga en cuenta que el ejemplo contiene una función de punto de entrada denominada `LibMain`, pero debe asignarle el nombre `DllMain` para que funcione con las bibliotecas en tiempo de ejecución de MFC y C.

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)<br/>
[Punto de entrada de DllMain](/windows/win32/Dlls/dllmain)<br/>
[Procedimientos recomendados de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-best-practices)

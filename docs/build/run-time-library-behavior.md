---
title: "Archivos DLL y el comportamiento de la biblioteca de tiempo de ejecución de Visual C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 75bf84eeaf9277c5cf037c4fa59c28d109d95856
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Archivos DLL y el comportamiento de la biblioteca de tiempo de ejecución de Visual C++  
  
Cuando se compila una biblioteca de vínculos dinámicos (DLL) mediante el uso de Visual C++, de forma predeterminada, el vinculador incluye la biblioteca de tiempo de ejecución de Visual C++ (VCRuntime). VCRuntime contiene código necesario para inicializar y finalizar un ejecutable de C o C++. Cuando están vinculados en un archivo DLL, el código de VCRuntime proporciona una función de punto de entrada DLL interna denominada `_DllMainCRTStartup` que controla los mensajes de sistema operativo Windows para el archivo DLL para asociar o desasociar de un proceso o subproceso. El `_DllMainCRTStartup` función realiza tareas esenciales como la seguridad de búfer de pila configurar la inicialización de la biblioteca en tiempo de ejecución (CRT) de C y la finalización y llama a constructores y destructores para los objetos estáticos y globales. `_DllMainCRTStartup`también llamadas a funciones para otras bibliotecas como WinRT, MFC y ATL para realizar sus propias inicialización y terminación de enlace. Sin esta inicialización, CRT y otras bibliotecas, así como las variables estáticas, quedaría en un estado no inicializado. Si el archivo DLL usa un CRT vinculado estáticamente o un archivo DLL de CRT vinculado dinámicamente, se denominan los mismo VCRuntime interno de inicialización y las rutinas de terminación.  
  
## <a name="default-dll-entry-point-dllmaincrtstartup"></a>Predeterminado _DllMainCRTStartup de punto de entrada DLL  
  
En Windows, todos los archivos DLL pueden contener una función de punto de entrada opcional, normalmente denominada `DllMain`, que se llama para la inicialización y terminación. Esto le ofrece la oportunidad de asignar o liberar recursos adicionales según sea necesario. Windows llama a la función de punto de entrada en cuatro situaciones: asociación de procesos, desasociación de procesos, asociación de subprocesos y desasociación de subprocesos. Cuando un archivo DLL se carga en un espacio de direcciones del proceso, cuando se carga una aplicación que lo utiliza, o cuando la aplicación solicita el archivo DLL en tiempo de ejecución, el sistema operativo crea una copia independiente de los datos del archivo DLL. Esto se denomina *asociación de procesos*. *Asociación de subprocesos* se produce cuando el proceso de cargar la DLL en crea un nuevo subproceso. *Desasociación de subprocesos* se produce cuando finaliza el subproceso, y *desasociación de procesos* es cuando el archivo DLL ya no es necesario y se publica una aplicación. El sistema operativo realiza una llamada independiente al punto de entrada DLL para cada uno de estos eventos, pasando una *motivo* argumento para cada tipo de evento. Por ejemplo, el sistema operativo envía `DLL_PROCESS_ATTACH` como el *motivo* argumento para indicar el proceso de adjuntar.  
  
La biblioteca de VCRuntime proporciona una función de punto de entrada denominada `_DllMainCRTStartup` para controlar las operaciones de inicialización y finalización de forma predeterminada. En el proceso de adjuntar, la `_DllMainCRTStartup` función establece los controles de seguridad de búfer, inicializa el CRT y otras bibliotecas, inicializa la información de tipo de tiempo de ejecución, inicializa y llama a constructores de datos estáticos y no local, inicializa el almacenamiento local de subprocesos , incrementa un contador interno estático para cada operación de adjuntar y, a continuación, llama a una o biblioteca-proporcionados por el usuario `DllMain`. En el proceso de desasociación, la función se lleva a cabo estos pasos en orden inverso. Llama `DllMain`, disminuye el contador interno, llama a destructores, registrado y las funciones de terminación de CRT las llamadas `atexit` las funciones y notifica a las otras bibliotecas de terminación. Cuando el contador de datos adjuntos llega a cero, la función devuelve `FALSE` para indicar a Windows que se puede descargar el archivo DLL. El `_DllMainCRTStartup` función también se llama durante el subproceso de adjuntar y separar de subproceso. En estos casos, el código de VCRuntime no realiza ninguna inicialización ni la finalización por sí mismo y simplemente llama `DllMain` para pasar el mensaje a lo largo. Si `DllMain` devuelve `FALSE` del proceso de adjuntar, error, de señalización `_DllMainCRTStartup` llamadas `DllMain` nuevo y pasa `DLL_PROCESS_DETACH` como el *motivo* argumento, a continuación, pasa por el resto de la proceso de finalización.  
  
Al generar archivos DLL en Visual C++, el punto de entrada predeterminado `_DllMainCRTStartup` proporcionado por VCRuntime se vinculará automáticamente. No es necesario especificar una función de punto de entrada para el archivo DLL mediante la [/ENTRY (símbolo de punto de entrada)](../build/reference/entry-entry-point-symbol.md) opción del vinculador.  
  
> [!NOTE]
> Aunque es posible especificar otra función de punto de entrada para un archivo DLL mediante la/Entry: opción del vinculador, no se recomienda, ya que la función de punto de entrada tendría que duplicar todo lo que `_DllMainCRTStartup` es así, en el mismo orden. VCRuntime proporciona funciones que le permiten duplicar su comportamiento. Por ejemplo, puede llamar a [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) inmediatamente en el proceso de adjuntar para admitir la [/GS (comprobación de seguridad de búfer)](../build/reference/gs-buffer-security-check.md) opción de comprobación del búfer. Puede llamar a la `_CRT_INIT` función, pasando los mismos parámetros que la función de punto de entrada, para realizar el resto de las funciones de inicialización ni la finalización de la DLL.  
  
<a name="initializing-a-dll"></a>  
  
## <a name="initialize-a-dll"></a>Inicializar un archivo DLL  
  
El archivo DLL puede incluir el código de inicialización que se debe ejecutar cuando se cargue el archivo DLL. En orden para realizar sus propias funciones de inicialización y terminación de DLL, `_DllMainCRTStartup` llama a una función denominada `DllMain` que puede proporcionar. El `DllMain` debe tener la firma requerida para un punto de entrada DLL. La función de punto de entrada predeterminado `_DllMainCRTStartup` llamadas `DllMain` utilizando los mismos parámetros pasados por Windows. De forma predeterminada, si no se proporciona un `DllMain` (función), Visual C++ proporciona uno y vínculos en modo que `_DllMainCRTStartup` siempre tenga una función para llamar a. Esto significa que si no tiene que inicializar el archivo DLL, no hay nada especial que tiene que hacer cuando se crea el archivo DLL.  
  
Se trata de la firma que se usa para `DllMain`:  
  
```cpp  
#include <windows.h>  
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```  
  
Algunas bibliotecas encapsulan el `DllMain` función automáticamente. Por ejemplo, en una DLL de MFC normal, implemente el `CWinApp` del objeto `InitInstance` y `ExitInstance` funciones de miembro para realizar la inicialización y terminación requeridas por la DLL. Para obtener más información, consulte el [regular inicializar archivos DLL de MFC](#initializing-regular-dlls) sección.  
  
> [!WARNING]
> Hay límites significativos en lo que puede hacer con seguridad en un punto de entrada DLL. Vea [procedimientos recomendados generales](https://msdn.microsoft.com/library/windows/desktop/dn633971#general_best_practices) de determinadas API de Windows que no son seguros para llamar a en `DllMain`. Si necesita nada pero, a continuación, la inicialización más sencilla hacer esto en una función de inicialización para el archivo DLL. Puede exigir que las aplicaciones llamen a la función de inicialización después de `DllMain` se ejecute y antes de llame a otras funciones del archivo DLL.  
  
<a name="initializing-non-mfc-dlls"></a>  
  
### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializar archivos DLL normales (no basada en MFC)  
  
Para realizar su propia inicialización de DLL de normal (no basada en MFC) que usan el VCRuntime proporcionado por el `_DllMainCRTStartup` punto de entrada, el código de origen de archivo DLL debe contener una función denominada `DllMain`. El código siguiente presenta una estructura básica que muestra qué la definición de `DllMain` podría ser similar:  
  
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
> Documentación del SDK de Windows anterior indica que el nombre real de la función de punto de entrada DLL debe especificarse en el vinculador de línea de comandos con la opción/Entry. Con Visual C++, no es necesario usar la opción/ENTRY si el nombre de la función de punto de entrada es `DllMain`. De hecho, si utiliza la opción/Entry y el nombre de su punto de entrada función algo distinto de `DllMain`, CRT no se inicialicen correctamente a menos que la función de punto de entrada realiza las mismas llamadas de inicialización que `_DllMainCRTStartup` hace.  
  
<a name="initializing-regular-dlls"></a>  
  
### <a name="initialize-regular-mfc-dlls"></a>Inicializar archivos DLL de MFC estándar  
  
Porque tiene archivos DLL de MFC estándar un `CWinApp` objeto, deben realizar sus tareas de inicialización y finalización en la misma ubicación que una aplicación MFC: en el `InitInstance` y `ExitInstance` las funciones miembro de la DLL `CWinApp`-derivados clase. Debido a que MFC proporciona una `DllMain` función que llama a `_DllMainCRTStartup` para `DLL_PROCESS_ATTACH` y `DLL_PROCESS_DETACH`, no debe escribir el suyo propio `DllMain` función. MFC proporcionados por el `DllMain` llamadas a funciones `InitInstance` cuando se cargue el archivo DLL y llama a `ExitInstance` antes de que se descarga el archivo DLL.  
  
Una DLL de MFC normal puede realizar un seguimiento de varios subprocesos llamando a [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) y [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) en su `InitInstance` función. Estas funciones permiten la DLL para poder realizar un seguimiento de los datos específicos del subproceso.  
  
En la DLL de MFC normal que se vincula dinámicamente a MFC, si está utilizando MFC OLE, MFC Database (o DAO) o admite Sockets de MFC, respectivamente, la depuración MFCO de archivos DLL de extensión de MFC*versión*D.dll, MFCD*versión*D.dll y MFCN*versión*D.dll (donde *versión* es el número de versión) se vincularán automáticamente. Debe llamar a una de las siguientes funciones de inicialización predefinidas para cada uno de estos archivos DLL que se utilizan en su MFC DLL regular `CWinApp::InitInstance`.  
  
|Tipo de compatibilidad con MFC|Función de inicialización para llamar a|  
|-------------------------|-------------------------------------|  
|OLE de MFC (MFCO*versión*D.dll)|`AfxOleInitModule`|  
|Base de datos MFC (MFCD*versión*D.dll)|`AfxDbInitModule`|  
|Sockets de MFC (MFCN*versión*D.dll)|`AfxNetInitModule`|  
  
<a name="initializing-extension-dlls"></a>  
  
### <a name="initialize-mfc-extension-dlls"></a>Inicializar archivos DLL de extensión MFC  
  
Dado de extensión de MFC DLL no tiene un `CWinApp`-derivado del objeto (como los archivos DLL de MFC estándar), debe agregar el código de inicialización y finalización para el `DllMain` función que genera el Asistente para archivos DLL de MFC.  
  
 El asistente proporciona el código siguiente para archivos DLL de extensión MFC. En el código, `PROJNAME` es un marcador de posición para el nombre del proyecto.  
  
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
  
Crear un nuevo `CDynLinkLibrary` objeto durante la inicialización permite que la extensión MFC DLL para exportar `CRuntimeClass` objetos o recursos a la aplicación cliente.  
  
Si va a utilizar el archivo DLL desde archivos DLL de MFC estándar de uno o más de extensión MFC, debe exportar una función de inicialización que crea un `CDynLinkLibrary` objeto. Esa función debe llamarse desde cada uno de los archivos DLL de MFC que utilizan el archivo DLL de extensión MFC. Es un lugar adecuado para llamar a esta función de inicialización en el `InitInstance` función miembro de la MFC DLL regular `CWinApp`-objeto derivado antes de utilizar cualquiera de las clases exportadas o funciones de la DLL de extensión MFC.  
  
En el `DllMain` que genera el Asistente para archivos DLL de MFC, la llamada a `AfxInitExtensionModule` captura clases en tiempo de ejecución del módulo (`CRuntimeClass` estructuras), así como los generadores de objetos (`COleObjectFactory` objetos) para usar cuando el `CDynLinkLibrary` se crea el objeto. Debe comprobar el valor devuelto de `AfxInitExtensionModule`; si se devuelve un valor cero de `AfxInitExtensionModule`, deberá devolver cero su `DllMain` función.  
  
Si el archivo DLL de extensión MFC se vinculará explícitamente a un archivo ejecutable (lo que significa que el ejecutable llama `AfxLoadLibrary` para vincular al archivo DLL), debe agregar una llamada a `AfxTermExtensionModule` en `DLL_PROCESS_DETACH`. Esta función permite la biblioteca MFC limpiar el archivo DLL de extensión MFC cuando cada proceso que se separa de la DLL de extensión MFC (algo que tiene lugar cuando se cierra el proceso o cuando se descarga el archivo DLL como resultado de una `AfxFreeLibrary` llamadas). Si el archivo DLL de extensión MFC se vinculará implícitamente a la aplicación, la llamada a `AfxTermExtensionModule` no es necesario.  
  
Las aplicaciones que se debe llamar explícitamente vincular a archivos DLL de extensión MFC `AfxTermExtensionModule` al liberar el archivo DLL. También deben usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de las funciones de Win32 `LoadLibrary` y `FreeLibrary`) si la aplicación utiliza varios subprocesos. Usar `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y cierre que se ejecuta cuando la extensión MFC DLL se cargan y descargan no dañe el estado global de MFC.  
  
Porque MFCx0.dll ya está completamente inicializado por el tiempo `DllMain` es llama, puede asignar memoria y llamar a funciones MFC dentro de `DllMain` (a diferencia de la versión de 16 bits de MFC).  
  
Archivos DLL de extensión pueden ocuparse de multithreading controlando el `DLL_THREAD_ATTACH` y `DLL_THREAD_DETACH` casos en los `DllMain` función. Estos casos se pasan a `DllMain` cuando los subprocesos de adjuntar y separar desde el archivo DLL. Al llamar a [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) cuando se está asociando un archivo DLL permite que la DLL mantener el subproceso de índices de almacenamiento local (TLS) para cada subproceso asociado al archivo DLL.  
  
Tenga en cuenta que el archivo de encabezado Afxdllx.h contiene definiciones especiales para las estructuras utilizadas en archivos DLL de extensión MFC, como la definición de `AFX_EXTENSION_MODULE` y `CDynLinkLibrary`. Debe incluir este archivo de encabezado en el archivo DLL de extensión MFC.  
  
> [!NOTE]
>  Es importante que no defina ni anular la definición de cualquiera de los `_AFX_NO_XXX` macros en Stdafx.h. Estas macros existen solo con el fin de comprobar si una plataforma de destino determinado es compatible con esta característica o no. Puede escribir el programa para comprobar estas macros (por ejemplo, `#ifndef _AFX_NO_OLE_SUPPORT`), pero el programa nunca debe definir o anular la definición de estas macros.  
  
Una función de inicialización de ejemplo que se incluye identificadores de multithreading en [utilizar almacenamiento Local de subprocesos en una biblioteca de vínculos dinámicos](http://msdn.microsoft.com/library/windows/desktop/ms686997) del SDK de Windows. Tenga en cuenta que el ejemplo contiene una función de punto de entrada denominada `LibMain`, pero debe asignarle el nombre de esta función `DllMain` para que funcione con las bibliotecas de tiempo de ejecución de C y MFC.  
  
## <a name="see-also"></a>Vea también  
  
[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)  
[Punto de entrada de DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583.aspx)  
[Prácticas recomendadas de biblioteca de vínculos dinámicos](https://msdn.microsoft.com/library/windows/desktop/dn633971.aspx)  
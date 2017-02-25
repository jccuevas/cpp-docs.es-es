---
title: "Inicializar archivos DLL de extensi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], extensión"
  - "DLL de extensión [C++], inicializar"
  - "inicializar DLL"
ms.assetid: 08ad0381-3808-4bea-a93c-c9ba62496543
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Inicializar archivos DLL de extensi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como los archivos DLL de extensión no incluyen un objeto derivado de `CWinApp` \(como los archivos DLL estándar\), debe agregar el código de inicialización y finalización a la función `DllMain` generada por el Asistente para archivos DLL de MFC.  
  
 El asistente proporciona el siguiente fragmento de código para los archivos DLL de extensión.  En el código, `PROJNAME` es un marcador del nombre del proyecto.  
  
```  
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
  
      // Extension DLL one-time initialization  
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
  
 Si crea un objeto **CDynLinkLibrary** nuevo durante la inicialización, permitirá al archivo DLL de extensión exportar objetos o recursos `CRuntimeClass` a la aplicación de cliente.  
  
 Si va a utilizar el archivo DLL de extensión desde uno o más archivos DLL estándar, deberá exportar una función de inicialización que cree un objeto **CDynLinkLibrary**.  Esa función debe llamarse desde cualquier archivo DLL estándar que utilice el archivo DLL de extensión.  Un lugar apropiado para llamar a esta función de inicialización es la función miembro `InitInstance` del objeto derivado de `CWinApp` del archivo DLL estándar antes de utilizar cualquiera de las clases o funciones exportadas del archivo DLL de extensión.  
  
 En la función `DllMain` generada por el Asistente para archivos DLL de MFC, la llamada a `AfxInitExtensionModule` captura las clases en tiempo de ejecución del módulo \(estructuras `CRuntimeClass`\) así como todos los generadores de objetos \(objetos `COleObjectFactory`\) para utilizarlos cuando se cree el objeto **CDynLinkLibrary**.  Debe comprobar el valor devuelto por `AfxInitExtensionModule`; si `AfxInitExtensionModule` devuelve un valor cero, la función `DllMain` deberá devolver cero.  
  
 Si el archivo DLL de extensión va a vincularse explícitamente a un archivo ejecutable \(lo que significa que el ejecutable llama a `AfxLoadLibrary` para vincularla al archivo DLL\), debe agregar una llamada a `AfxTermExtensionModule` en **DLL\_PROCESS\_DETACH**.  Esta función permite a la biblioteca MFC limpiar el archivo DLL de extensión cuando todos los procesos se desasocian del mismo \(esto ocurre cuando finaliza el proceso o cuando se descarga el archivo DLL como resultado de una llamada a `AfxFreeLibrary`\).  Si el archivo DLL de extensión va a vincularse implícitamente a la aplicación, la llamada a `AfxTermExtensionModule` no es necesaria.  
  
 Las aplicaciones que se vinculen explícitamente a archivos DLL de extensión deberán llamar a **AfxTermExtensionModule** al liberar el archivo DLL.  También deben utilizar `AfxLoadLibrary` y `AfxFreeLibrary` \(en lugar de las funciones **LoadLibrary** y **FreeLibrary** de Win32\) si la aplicación utiliza varios subprocesos.  El uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y de cierre que se ejecuta cuando se carga o descarga el archivo DLL de extensión no dañe el estado global de MFC.  
  
 Como el archivo MFCx0.dll ya está completamente inicializado cuando se llama a `DllMain`, es posible asignar memoria y llamar a funciones de MFC dentro de `DllMain` \(a diferencia de lo que ocurría en la versión de 16 bits de MFC\).  
  
 Los archivos DLL de extensión pueden controlar el multithreading controlando los casos **DLL\_THREAD\_ATTACH** y **DLL\_THREAD\_DETACH** en la función `DllMain`.  Estos casos se pasan a `DllMain` cuando se asocian subprocesos a un archivo DLL y cuando se desasocian del mismo.  Si se llama a [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) cuando se está asociando un archivo DLL, se permite a dicho archivo mantener índices de almacenamiento local de subprocesos \(TLS, Thread Local Storage\) para cada subproceso asociado al archivo DLL.  
  
 Tenga en cuenta que el archivo de encabezado Afxdllx.h contiene definiciones especiales para las estructuras que se utilizan en los archivos DLL de extensión, como la definición de `AFX_EXTENSION_MODULE` y **CDynLinkLibrary**.  Deberá incluir este archivo de encabezado en el archivo DLL de extensión.  
  
> [!NOTE]
>  Es importante que no defina ni elimine la definición de ninguna de las macros \_AFX\_NO\_XXX de Stdafx.h.  Para obtener más información, vea el artículo "PRB: Problems Occur When Defining \_AFX\_NO\_XXX" \(Q140751\) de Knowledge Base.  Encontrará artículos de Knowledge Base en MSDN Library o en [http:\/\/search.support.microsoft.com\/](http://search.support.microsoft.com/).  
  
 En el tema [Utilizar almacenamiento local de subprocesos en una biblioteca de vínculos dinámicos](http://msdn.microsoft.com/library/windows/desktop/ms686997) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)], se incluye una función de inicialización de ejemplo que controla el uso del multithreading.  Tenga en cuenta que la función de ejemplo contiene una función de punto de entrada denominada **LibMain**, pero debe asignarle el nombre `DllMain` para que funcione con MFC y las bibliotecas en tiempo de ejecución de C.  
  
 El ejemplo [DLLHUSK](http://msdn.microsoft.com/es-es/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) de MFC ilustra el uso de las funciones de inicialización.  
  
## ¿Qué desea hacer?  
  
-   [Inicializar archivos DLL estándar](../build/initializing-regular-dlls.md)  
  
-   [Inicializar archivos DLL que no están basados en MFC](../build/initializing-non-mfc-dlls.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Comportamiento de la biblioteca en tiempo de ejecución de C y \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [Utilizar archivos DLL de extensión de base de datos, OLE y Sockets en archivos DLL estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [\<caps:sentence id\="tgt34" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>Especificación de funciones para DllMain \(SDK de Windows\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt35" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>Función de punto de entrada de biblioteca de vínculos dinámicos \(SDK de Windows\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
## Vea también  
 [Inicializar un archivo DLL](../build/initializing-a-dll.md)
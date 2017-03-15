---
title: "Inicializar archivos DLL est&#225;ndar | Microsoft Docs"
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
  - "DLL [C++], estándar"
  - "inicializar DLL"
  - "DLL estándar [C++], inicializar"
ms.assetid: f1f091d1-bb91-468a-94f4-3c554657b8fc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Inicializar archivos DLL est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como los archivos DLL estándar incluyen un objeto `CWinApp`, deben realizar sus tareas de inicialización y finalización en la misma ubicación que una aplicación MFC: en las funciones miembro `InitInstance` y **ExitInstance**  de la clase derivada de `CWinApp` del archivo DLL.  Como MFC proporciona una función `DllMain` invocada por **\_DllMainCRTStartup** para **PROCESS\_ATTACH** y **PROCESS\_DETACH**, no debe escribir su propia función `DllMain`.  La función `DllMain` proporcionada por MFC llamará a `InitInstance` cuando se cargue el archivo DLL y a `ExitInstance` antes de descargar el archivo DLL.  
  
 Un archivo DLL estándar puede hacer un seguimiento de varios subprocesos llamando a [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) y [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) en la función `InitInstance`.  Estas funciones permiten al archivo DLL hacer un seguimiento de datos específicos del subproceso.  
  
 Si utiliza la compatibilidad con MFC OLE, MFC Database \(o DAO\) o MFC Sockets en el archivo DLL estándar que se vincula dinámicamente a MFC, se vincularán automáticamente los archivos DLL de extensión para depuración de MFC MFCOxxD.dll, MFCDxxD.dll y MFCNxxD.dll \(donde xx es el número de versión\), respectivamente.  Debe llamar a una de las siguientes funciones de inicialización predefinidas para cada uno de estos archivos DLL que se utilizan en la función `CWinApp::InitInstance` del archivo DLL estándar.  
  
|Tipo de compatibilidad con MFC|Función de inicialización que se debe llamar|  
|------------------------------------|--------------------------------------------------|  
|MFC OLE \(MFCOxxD.dll\)|`AfxOleInitModule`|  
|MFC Database \(MFCDxxD.dll\)|`AfxDbInitModule`|  
|MFC Sockets \(MFCNxxD.dll\)|`AfxNetInitModule`|  
  
## ¿Qué desea hacer?  
  
-   [Inicializar archivos DLL de extensión](../build/initializing-extension-dlls.md)  
  
-   [Inicializar archivos DLL que no están basados en MFC](../build/initializing-non-mfc-dlls.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Comportamiento de la biblioteca en tiempo de ejecución de C y \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [Utilizar archivos DLL de extensión de base de datos, OLE y Sockets en archivos DLL estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [\<caps:sentence id\="tgt22" sentenceid\="704731be78a1b2b43311fed62656e454" class\="tgtSentence"\>Procesos y subprocesos \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
-   [Contenedores de almacenamiento local de subprocesos \(Nota técnica 58 de MFC\)](../mfc/tn058-mfc-module-state-implementation.md)  
  
## Vea también  
 [Inicializar un archivo DLL](../build/initializing-a-dll.md)
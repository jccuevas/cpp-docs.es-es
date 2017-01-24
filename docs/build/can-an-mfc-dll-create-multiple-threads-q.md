---
title: "&#191;Puede un archivo DLL de MFC crear varios subprocesos? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], multithreading"
  - "DLL de MFC [C++], multithreading"
  - "subprocesamiento múltiple [C++], DLL"
  - "subprocesamiento [MFC], DLL"
ms.assetid: 41d5b5e6-a7d3-42bf-b641-f1245abd1c59
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &#191;Puede un archivo DLL de MFC crear varios subprocesos?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Salvo durante la inicialización, un archivo DLL de MFC puede crear de forma segura varios subprocesos si utiliza funciones de almacenamiento local de subprocesos \(TLS, Thread Local Storage\) para Win32 como **TlsAlloc** a fin de asignar el almacenamiento local de subprocesos.  Sin embargo, si un archivo DLL de MFC utiliza **\_\_declspec\(thread\)** para asignar el almacenamiento local de subprocesos, la aplicación de cliente deberá vincularse implícitamente al archivo DLL.  Si la aplicación de cliente se vincula explícitamente al archivo DLL, la llamada a **LoadLibrary** no podrá cargar dicho archivo.  Para obtener más información sobre la forma de crear varios subprocesos dentro de archivos DLL de MFC, vea el artículo "PRB: Calling LoadLibrary\(\) to Load a DLL That Has Static TLS" \(Q118816\) de Knowledge Base.  
  
 Un archivo DLL de MFC que cree un subproceso MFC nuevo durante el inicio dejará de responder cuando lo cargue una aplicación.  Esto ocurrirá siempre que se cree un subproceso llamando a `AfxBeginThread` o `CWinThread::CreateThread` dentro de:  
  
-   La función `InitInstance` de un objeto derivado de `CWinApp` de un archivo DLL estándar.  
  
-   Una función `DllMain` o **RawDllMain** de un archivo DLL estándar.  
  
-   Una función `DllMain` o **RawDllMain** de un archivo DLL de extensión.  
  
 Para obtener más información sobre cómo crear subprocesos durante la inicialización, vea el artículo "PRB: Cannot Create an MFC Thread During DLL Startup" \(Q142243\) de Knowledge Base.  
  
## Vea también  
 [Preguntas más frecuentes sobre archivos DLL](../build/dll-frequently-asked-questions.md)
---
title: "Subprocesamiento m&#250;ltiple con C y Win32 | Microsoft Docs"
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
  - "subprocesamiento múltiple [C++], C y Win32"
  - "subprocesamiento [C]"
  - "subprocesamiento [C++], C y Win32"
  - "Visual C, multithreading"
  - "Win32 [C++], multithreading"
  - "aplicaciones Win32 [C++], multithreading"
  - "API de Windows [C++], multithreading"
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple con C y Win32
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Visual C\+\+ permite crear aplicaciones multiproceso con Microsoft Windows: Windows XP, Windows 2000, Windows NT, Windows Me y Windows 98.  Debería considerar la posibilidad de usar varios subprocesos si la aplicación necesita controlar múltiples actividades, tales como el uso simultáneo de teclado y mouse.  Un subproceso puede tratar la entrada desde el teclado, mientras que otro proceso filtra las actividades del mouse.  Un tercer subproceso puede actualizar la presentación en pantalla según los datos de los subprocesos del teclado y del mouse.  Al mismo tiempo, otros subprocesos pueden encargarse del acceso a archivos del disco o de obtener datos de un puerto de comunicaciones.  
  
 En Visual C\+\+, existen dos maneras de programar con múltiples subprocesos: utilizar la biblioteca MFC \(Microsoft Foundation Class\) o bien utilizar la biblioteca en tiempo de ejecución de C y la API Win32.  Para obtener información sobre cómo crear aplicaciones multiproceso con MFC, vea [Multithreading con C\+\+ y MFC](../parallel/multithreading-with-cpp-and-mfc.md) después de leer los temas siguientes sobre multithreading en C.  
  
 Estos temas describen las características de Visual C\+\+ que permiten la creación de programas multiproceso.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Qué es multithreading](../parallel/multithread-programs.md)  
  
-   [Compatibilidad de bibliotecas con multithreading](../parallel/library-support-for-multithreading.md)  
  
-   [Archivos de inclusión para multithreading](../parallel/include-files-for-multithreading.md)  
  
-   [Funciones de la biblioteca en tiempo de ejecución de C para el control de subprocesos](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [Ejemplo de programa multiproceso en C](../parallel/sample-multithread-c-program.md)  
  
-   [Crear un programa Win32 multiproceso](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [Compilar y vincular programas multiproceso](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [Evitar áreas de riesgo en programas multiproceso](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [Almacenamiento local de subprocesos \(TLS\)](../parallel/thread-local-storage-tls.md)  
  
## Vea también  
 [Compatibilidad del código antiguo con multithreading \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)
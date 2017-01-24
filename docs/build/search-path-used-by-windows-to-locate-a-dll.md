---
title: "Ruta de b&#250;squeda de Windows para encontrar un archivo DLL | Microsoft Docs"
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
  - "DLL [C++], ruta de búsqueda de Windows"
  - "buscar DLL"
  - "búsquedas de DLL conocidas [C++]"
  - "buscar DLLs"
  - "buscar rutas [C++]"
  - "buscar [C++], DLL"
  - "Windows [C++], ruta de búsqueda para encontrar un archivo DLL"
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Ruta de b&#250;squeda de Windows para encontrar un archivo DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tanto en la vinculación implícita como en la vinculación explícita, Windows busca primero "archivos DLL conocidos", como Kernel32.dll y User32.dll.  Después, Windows busca los archivos DLL en el orden siguiente:  
  
1.  El directorio que contiene el módulo ejecutable para el proceso actual.  
  
2.  El directorio actual.  
  
3.  El directorio del sistema de Windows.  La función **GetSystemDirectory** recupera la ruta de acceso de este directorio.  
  
4.  El directorio de Windows.  La función **GetWindowsDirectory** recupera la ruta de acceso de este directorio.  
  
5.  Los directorios mostrados en la variable de entorno PATH.  
  
    > [!NOTE]
    >  La variable de entorno LIBPATH no se utiliza.  
  
## ¿Qué desea hacer?  
  
-   [Vincular de forma implícita](../build/linking-implicitly.md)  
  
-   [Vincular de forma explícita](../build/linking-explicitly.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)
---
title: "Vincular un ejecutable a un archivo DLL | Microsoft Docs"
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
  - "DLL [C++], vincular"
  - "vinculación de carga dinámica [C++]"
  - "archivos ejecutables [C++], vincular a DLL"
  - "vinculación explícita [C++]"
  - "vinculación implícita [C++]"
  - "vincular [C++], DLL"
  - "cargar DLL [C++]"
  - "tiempo de ejecución [C++], vincular"
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Vincular un ejecutable a un archivo DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un archivo ejecutable puede vincularse a \(o cargar\) un archivo DLL de dos maneras distintas:  
  
-   [Vinculación implícita](../build/linking-implicitly.md)  
  
-   [Vinculación explícita](../build/linking-explicitly.md)  
  
 La vinculación implícita se denomina a veces carga estática o vinculación dinámica en tiempo de carga.  La vinculación explícita se denomina a veces carga dinámica o vinculación dinámica en tiempo de ejecución.  
  
 En la vinculación implícita, el archivo ejecutable que utiliza el archivo DLL se vincula a una biblioteca de importación \(archivo .lib\) proporcionada por el autor del archivo DLL.  El sistema operativo cargará el archivo DLL cuando se cargue el archivo ejecutable que lo utiliza.  El archivo ejecutable cliente llama a las funciones exportadas del archivo DLL como si éstas estuvieran dentro del ejecutable.  
  
 En la vinculación explícita, el archivo ejecutable que utiliza el archivo DLL debe hacer llamadas a función para cargar y descargar explícitamente el archivo DLL, así como para tener acceso a las funciones exportadas desde el archivo DLL.  El archivo ejecutable cliente debe llamar a las funciones exportadas mediante un puntero a función.  
  
 Un archivo ejecutable puede utilizar el mismo archivo DLL con cualquier método de vinculación.  Además, estos mecanismos no son mutuamente exclusivos, ya que un archivo ejecutable puede vincularse implícitamente a un archivo DLL mientras otro ejecutable puede asociarse al mismo archivo DLL explícitamente.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Trabajar con bibliotecas de importación y archivos de exportación](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
-   [La ruta de acceso de búsqueda que Windows utiliza para buscar una DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)
---
title: "Compilar y vincular programas multiproceso | Microsoft Docs"
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
  - "compilar programas multiproceso"
  - "compilar código fuente [C++], programas multiproceso"
  - "vincular [C++], programas multiproceso"
  - "subprocesamiento múltiple [C++], programas compilados"
  - "subprocesamiento múltiple [C++], vincular programas"
  - "subprocesamiento [C++], programas compilados"
  - "subprocesamiento [C++], vincular programas"
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compilar y vincular programas multiproceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El programa Bounce.c aparece en el [Ejemplo de programa multiproceso en C](../parallel/sample-multithread-c-program.md).  
  
 Los programas se compilan en modo multiproceso de forma predeterminada.  
  
#### Para compilar y vincular el programa multiproceso Bounce.c desde el entorno de desarrollo  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el panel **Tipos de proyecto**, haga clic en **Win32**.  
  
3.  En el panel **Plantillas**, haga clic en **Aplicación de consola Win32** y, a continuación, asigne un nombre al proyecto.  
  
4.  Agregue el archivo que contiene el código fuente de C al proyecto.  
  
5.  En el menú **Compilar**, haga clic en el comando **Compilar** para compilar el proyecto.  
  
#### Para compilar y vincular el programa multiproceso Bounce.c desde la línea de comandos  
  
1.  Compile y vincule el programa:  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## Vea también  
 [Subprocesamiento múltiple con C y Win32](../parallel/multithreading-with-c-and-win32.md)
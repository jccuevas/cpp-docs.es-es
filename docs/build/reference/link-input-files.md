---
title: "Archivos de entrada de LINK | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "entradas de comandos para los archivos del vinculador [C++]"
  - "archivos [C++], LINK"
  - "bibliotecas de importación [C++], archivos del vinculador"
  - "archivos de entrada [C++], LINK"
  - "LINK (herramienta) [C++], archivos de entrada"
  - "vinculador [C++], archivos de entrada"
  - "archivos de definición de módulos"
  - "archivos de definición de módulos, archivos del vinculador"
  - "recursos [C++], archivos del vinculador"
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos de entrada de LINK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El vinculador deberá recibir archivos que contengan objetos, bibliotecas estándar y de importación, recursos, definiciones de módulo y entradas de comandos.  LINK no usa las extensiones de archivo para realizar suposiciones sobre el contenido de los archivos.  En lugar de ello, examina cada archivo de entrada para averiguar a qué clase pertenece.  
  
 Los archivos objeto en la línea de comandos se procesan en el orden que aparecen en la línea de comandos.  También se busca en las bibliotecas en el orden de la línea de comandos, con la limitación siguiente: los símbolos que no están resueltos cuando se recibe un archivo objeto de una biblioteca se buscan primero en esa biblioteca, después, en las bibliotecas siguientes en la línea de comandos y directivas [\/DEFAULTLIB \(Especificar la biblioteca predeterminada\)](../../build/reference/defaultlib-specify-default-library.md) y, por último, en cualquier biblioteca que aparezca en el inicio de la línea de comandos.  
  
> [!NOTE]
>  LINK ya no acepta el punto y coma \(ni otro carácter\) como inicio de un comentario en los archivos de respuesta y de orden.  El punto y coma sólo se reconoce como inicio de un comentario en los archivos de definición de módulos \(.def\).  
  
 LINK usa los siguientes tipos de archivos de entrada:  
  
-   [archivos .obj](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [archivos .netmodule](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [archivos .lib](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [archivos .exp](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [archivos .def](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [archivos .pdb](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [archivos .res](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [archivos .exe](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [archivos .txt](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [archivos .ilk](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)
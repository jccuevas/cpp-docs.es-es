---
title: "Sintaxis de nombres de archivo de CL | Microsoft Docs"
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
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), sintaxis de los nombres de archivo"
  - "extensiones, especificar al compilador"
  - "nombres de archivo [C++]"
  - "nombres de archivo [C++], compilador CL"
  - "rutas de acceso, sintaxis de los nombres de archivo del compilador CL"
  - "sintaxis, nombre de archivo del compilador"
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Sintaxis de nombres de archivo de CL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CL acepta archivos con nombres que siguen las convenciones de nomenclatura FAT, HPFS o NTFS.  Todos los nombres de archivo pueden incluir una ruta de acceso completa o parcial.  Una ruta de acceso completa incluye un nombre de unidad y uno o más nombres de directorio.  CL acepta nombres de archivo separados por barras diagonales inversas \(\\\) o por barras diagonales \(\/\).  Los nombres de archivo que contienen espacios deben encerrarse entre comillas dobles.  Una ruta de acceso parcial omite el nombre de la unidad, que CL supone que es la unidad actual.  Si no se especifica una ruta de acceso, CL supone que el archivo se encuentra en el directorio actual.  
  
 La extensión del nombre de archivo determina cómo se procesan los archivos.  Los archivos de C y C\+\+, que tienen la extensión .c, .cxx o .cpp, se compilan.  Otros archivos, incluidos los archivos .obj, las bibliotecas \(.lib\) y los archivos de definición de módulos \(.def\), se transfieren al vinculador sin procesarse.  
  
## Vea también  
 [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)
---
title: "Archivos .Exp como entrada del vinculador | Microsoft Docs"
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
  - ".exp (archivos) [C++]"
  - "EXP (archivos)"
  - "exportar datos, archivos de exportación (.exp)"
  - "exportar funciones"
  - "exportar funciones, información sobre funciones exportadas"
  - "funciones [C++], exportar"
  - "bibliotecas de importación, archivos del vinculador"
  - "vincular [C++], exportaciones"
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos .Exp como entrada del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los archivos de exportación \(.exp\) contienen información sobre funciones exportadas y elementos de datos.  Cuando LIB crea una biblioteca de importación, también crea un archivo .exp.  Este archivo se usa cuando se vincula un programa que, directa o indirectamente, lleva a cabo acciones de exportación e importación con otro programa.  Al vincular con un archivo .exp, LINK no produce una biblioteca de importación pues asume que LIB ya ha creado una.  Para obtener más detalles acerca de los archivos .exp y las bibliotecas de importación, vea [Trabajar con bibliotecas de importación y archivos de exportación](../../build/reference/working-with-import-libraries-and-export-files.md).  
  
## Vea también  
 [Archivos de entrada de LINK](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)
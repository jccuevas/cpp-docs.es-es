---
title: "Crear el texto de un archivo en l&#237;nea | Microsoft Docs"
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
  - "archivos en línea, crear texto"
  - "NMAKE (programa), archivos en línea"
  - "texto, archivo en línea"
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Crear el texto de un archivo en l&#237;nea
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos en línea son temporales o permanentes.  
  
## Sintaxis  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## Comentarios  
 Se ha de especificar *inlinetext* en la primera línea después del comando.  Marca el final con corchetes angulares dobles \(\<\<\) al principio de una línea.  El archivo contiene todo el texto *inlinetext* delante de los corchetes delimitadores.  El texto *inlinetext* puede tener expansiones de macro y sustituciones, pero no directivas ni comentarios de archivo MAKE.  Los espacios, las tabulaciones y los caracteres de nueva línea se interpretan de forma literal.  
  
 Un archivo temporal existe mientras dure la sesión y puede ser utilizado de nuevo por otros comandos.  Se ha de especificar **KEEP** después de los corchetes angulares para conservar el archivo después de la sesión de NMAKE; un archivo sin nombre se conserva en el disco con el nombre de archivo generado.  Se ha de especificar **NOKEEP o nada para un archivo temporal.** KEEP y NOKEEP no distinguen entre mayúsculas y minúsculas.  
  
## Vea también  
 [Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)
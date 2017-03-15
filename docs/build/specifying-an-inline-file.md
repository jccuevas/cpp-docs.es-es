---
title: "Especificar un archivo insertado | Microsoft Docs"
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
  - "archivos [C++], inline"
  - "archivos insertados [C++], especificar NMAKE"
  - "NMAKE (programa), archivos en línea"
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Especificar un archivo insertado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifique dos corchetes angulares \(\<\<\) del comando donde debe aparecer *el nombre de archivo* .  Los corchetes angulares no pueden ser una expansión de macro.  
  
## Sintaxis  
  
```  
<<[filename]  
```  
  
## Comentarios  
 Cuando se ejecuta el comando, los corchetes angulares se reemplazan por *filename*, si se especifica, o por un nombre único generado por NMAKE.  Si se especifica, *filename* debe ir a continuación de los corchetes angulares sin espacios ni tabulaciones.  Se permite una ruta de acceso.  No se requiere ni se supone una extensión.  Si se especifica *filename*, el archivo se crea en el directorio actual o en el especificado, sobrescribiendo cualquier archivo existente con ese nombre; en caso contrario, se crea en el directorio TMP \(o en el directorio actual, si no se ha definido la variable de entorno TMP\).  Si se vuelve a utilizar un argumento *filename* anterior, NMAKE reemplaza el archivo anterior.  
  
## Vea también  
 [Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)
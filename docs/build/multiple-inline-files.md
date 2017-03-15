---
title: "M&#250;ltiples archivos en l&#237;nea | Microsoft Docs"
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
  - "archivos en línea, varios NMAKE"
  - "varios archivos en línea"
  - "NMAKE (programa), archivos en línea"
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# M&#250;ltiples archivos en l&#237;nea
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un comando puede crear más de un archivo en línea.  
  
## Sintaxis  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## Comentarios  
 Para cada archivo, se han de especificar una o más líneas de texto en línea seguidas de una línea de cierre que contenga el delimitador.  El texto del segundo archivo se ha de empezar en la línea que sigue a la línea delimitadora del primer archivo.  
  
## Vea también  
 [Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)
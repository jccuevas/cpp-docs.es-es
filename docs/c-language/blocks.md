---
title: "Bloques | Microsoft Docs"
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
  - "bloques"
  - "instrucciones compuestas"
  - "definiciones de funciones, bloques en código"
  - "instrucciones, compuesta"
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Bloques
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una secuencia de declaraciones, definiciones e instrucciones delimitada por llaves \(**{ }**\) se denomina “bloque”. Hay dos tipos de bloques en C.  La “instrucción compuesta”, una instrucción compuesta de una o más instrucciones \(vea [La instrucción compuesta](../c-language/compound-statement-c.md)\), es un tipo de bloque.  El otro, la “definición de función”, consta de una instrucción compuesta \(el cuerpo de la función\) más el “encabezado” asociado de la función \(el nombre de la función, el tipo de valor devuelto y los parámetros formales\).  De un bloque ubicado dentro de otros bloques se dice que está “anidado”.  
  
 Observe que aunque todas las instrucciones compuestas se encuentran entre llaves, no todo lo que hay dentro de las llaves constituye una instrucción compuesta.  Por ejemplo, aunque las especificaciones de elementos de matriz, estructura o enumeración pueden aparecer entre llaves, no son instrucciones compuestas.  
  
## Vea también  
 [Archivos de código fuente y programas de origen](../c-language/source-files-and-source-programs.md)
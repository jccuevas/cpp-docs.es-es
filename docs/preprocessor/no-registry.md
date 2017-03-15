---
title: "no_registry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_registry (atributo)"
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# no_registry
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`no_registry` indica al compilador que no busque en el registro bibliotecas de tipos importadas con `#import`.  
  
## Sintaxis  
  
```  
  
#import filename no_registry  
```  
  
#### Parámetros  
 *filename*  
 Una biblioteca de tipos.  
  
## Comentarios  
 Si una biblioteca de tipos a la que se hace referencia no se encuentra en los directorios de inclusión, la compilación producirá un error aunque la biblioteca de tipos esté en el registro. `no_registry` se propaga a otras bibliotecas de tipos importadas implícitamente con `auto_search`.  
  
 El compilador nunca buscará en el registro bibliotecas de tipos especificadas por nombre de archivo y que se hayan pasado directamente a `#import`.  
  
 Cuando se especifica `auto_search`, los `#import` adicionales aparecerán con la configuración `no_registry` del `#import` inicial \(si la directiva `#import` inicial era `no_registry`, un `#import` generado mediante `auto_search` también es `no_registry`.\)  
  
 `no_registry` es útil si se desea importar bibliotecas de tipos de referencias cruzadas sin el riesgo de que el compilador encuentre una versión anterior del archivo en el registro. `no_registry` también es útil si la biblioteca de tipos no está registrada.  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)
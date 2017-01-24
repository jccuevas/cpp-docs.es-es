---
title: "optimize | Microsoft Docs"
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
  - "vc-pragma.optimize"
  - "optimize_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "optimize (pragma)"
  - "pragma (directivas), optimize"
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# optimize
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica las optimizaciones que se efectuarán función por función.  
  
## Sintaxis  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## Comentarios  
 La directiva pragma **optimize** debe aparecer fuera de una función y tiene efecto en la primera función definida después de que se vea la directiva pragma.  Los argumentos **on** y **off** activan o desactivan opciones especificadas en *optimization\-list*.  
  
 La lista *optimization\-list* pueden contener cero o más de los parámetros que se muestran en la tabla siguiente.  
  
### Parámetros de la directiva pragma optimize  
  
|Parámetros|Tipo de optimización|  
|----------------|--------------------------|  
|**g**|Habilitar optimizaciones globales.|  
|**s** o **t**|Especificar secuencias cortas o rápidas de código máquina.|  
|**y**|Generar punteros de marco en la pila del programa.|  
  
 Son las mismas letras usadas con las opciones del compilador [O](../build/reference/o-options-optimize-code.md).  Por ejemplo, la directiva pragma siguiente es equivalente a la opción del compilador **\/Os**:  
  
```  
#pragma optimize( "ts", on )  
```  
  
 El uso de la directiva pragma **optimize** con la cadena vacía \(**""**\) es una forma especial de la directiva:  
  
 Cuando se utiliza el parámetro **off**, desactiva las optimizaciones, enumeradas en la tabla anterior de este tema.  
  
 Cuando se usa el parámetro **on**, restablece las optimizaciones a las que especificó con la opción del compilador [\/O](../build/reference/o-options-optimize-code.md).  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
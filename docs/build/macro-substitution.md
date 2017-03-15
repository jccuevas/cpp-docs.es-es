---
title: "Sustituci&#243;n de macros | Microsoft Docs"
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
  - "macros, NMAKE"
  - "NMAKE (programa), sustitución de macros"
  - "macros de sustitución en NMAKE"
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Sustituci&#243;n de macros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se llama a *macroname*, cada repetición de *string1* en su cadena de definición se reemplaza por *string2.*  
  
## Sintaxis  
  
```  
$(macroname:string1=string2)  
```  
  
## Comentarios  
 La sustitución de macros distingue entre mayúsculas y minúsculas, y es literal; *string1* y *string2* no pueden llamar a macros.  La sustitución no modifica la definición original.  Se puede sustituir texto en cualquier macro predefinida excepto [$$@](../build/filename-macros.md).  
  
 Delante del signo de dos puntos no hay espacios ni tabulaciones; los caracteres situados detrás del signo de dos puntos se interpretan como literales.  Si el valor de *string2* es nulo, todas las repeticiones de *string1* se eliminan de la cadena de definición de la macro.  
  
## Vea también  
 [Utilizar una macro NMAKE](../build/using-an-nmake-macro.md)
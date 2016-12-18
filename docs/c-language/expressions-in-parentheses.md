---
title: "Expresiones entre par&#233;ntesis | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "evaluación de expresiones, orden de evaluación"
  - "expresiones [C++], evaluar"
  - "paréntesis"
  - "paréntesis, expresiones"
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Expresiones entre par&#233;ntesis
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede agregar cualquier operando entre paréntesis sin cambiar el tipo o el valor de la expresión incluida.  Por ejemplo, en la expresión:  
  
```  
( 10 + 5 ) / 5  
```  
  
 los paréntesis alrededor de `10 + 5` indican que el valor de `10 + 5` se evalúa primero y se convierte en el operando izquierdo del operador de división \(**\/**\).  El resultado de `( 10 + 5 ) / 5` es 3.  Sin paréntesis, `10 + 5 / 5` se evaluaría como 11.  
  
 Aunque los paréntesis afectan a la manera en que los operandos se agrupan en una expresión, no se puede garantizar un orden concreto de evaluación en todos los casos.  Por ejemplo, ni los paréntesis ni la agrupación de izquierda a derecha de la expresión siguiente garantiza cuál será el valor de `i` en cualquiera de las subexpresiones:  
  
```  
( i++ +1 ) * ( 2 + i )  
```  
  
 El compilador es libre de evaluar los dos lados de la multiplicación en cualquier orden.  Si el valor inicial de `i` es cero, la expresión completa se podría evaluar como cualquiera de estas dos instrucciones:  
  
```  
( 0 + 1 + 1 ) * ( 2 + 1 )   
( 0 + 1 + 1 ) * ( 2 + 0 )  
```  
  
 Las excepciones resultantes de los efectos secundarios se tratan en [Efectos secundarios](../c-language/side-effects.md).  
  
## Vea también  
 [Expresiones primarias de C](../c-language/c-primary-expressions.md)
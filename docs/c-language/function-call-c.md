---
title: "Llamada de funci&#243;n (C) | Microsoft Docs"
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
  - "llamadas a funciones"
  - "llamadas a funciones, funciones de C"
  - "funciones [C], llamar"
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Llamada de funci&#243;n (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una “llamada a función” es una expresión que incluye el nombre de la función que se llama o el valor de un puntero a función y, opcionalmente, los argumentos que se pasan a la función.  
  
## Sintaxis  
 *postfix\-expression*:  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *argument\-expression\-list*:  
 *assignment\-expression*  
  
 *argument\-expression\-list*  **,**  *assignment\-expression*  
  
 El elemento *postfix\-expression* se debe evaluar como una dirección de función \(por ejemplo, un identificador de función o el valor de un puntero a función\) y *argument\-expression\-list* es una lista de expresiones \(separadas por comas\) cuyos valores \(los "argumentos"\) se pasan a la función.  El elemento *argument\-expression\-list* puede estar vacío.  
  
 Una expresión de llamada a función tiene el valor y el tipo del valor devuelto de la función.  Una función no puede devolver un objeto de tipo de matriz.  Si el tipo de valor devuelto de la función es `void` \(es decir, la función nunca se ha declarado para devolver un valor\), la expresión de llamada a función también tiene el tipo `void`. \(Vea [Llamadas a función](../c-language/function-calls.md) para obtener más información\).  
  
## Vea también  
 [Operador de llamada de función: \(\)](../cpp/function-call-operator-parens.md)
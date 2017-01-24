---
title: "Asignaci&#243;n compuesta de C | Microsoft Docs"
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
  - "operadores de asignación, compuesta"
  - "operadores de asignación compuesta"
  - "operadores [C], asignación"
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asignaci&#243;n compuesta de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores de asignación compuesta combinan el operador de la asignación simple con otro operador binario.  Los operadores de asignación compuesta realizan la operación especificada por el operador adicional y, a continuación, asignan el resultado al operando izquierdo.  Por ejemplo, una expresión de asignación compuesta tal como  
  
```  
  
expression1 += expression2  
```  
  
 puede entenderse como  
  
```  
  
expression1 = expression1 + expression2  
```  
  
 Sin embargo, la expresión de asignación compuesta no es equivalente a la versión expandida porque la expresión de asignación compuesta evalúa *expression1* una sola vez, mientras que la versión expandida evalúa *expression1* dos veces: en la operación de suma y en la operación de asignación.  
  
 Los operandos de un operador de asignación compuesta deben ser de tipo entero o flotante.  Cada operador de asignación compuesta realiza las conversiones que realiza el operador binario correspondiente y restringe los tipos de sus operandos en consecuencia.  Los operadores de suma y asignación \(`+=`\) y resta y asignación \(**–\=**\) también pueden tener un operando izquierdo de tipo de puntero, en cuyo caso el operando derecho debe ser de tipo entero.  El resultado de una operación de asignación compuesta tiene el valor y el tipo del operando izquierdo.  
  
```  
#define MASK 0xff00  
  
n &= MASK;  
```  
  
 En este ejemplo, se realiza una operación AND inclusiva bit a bit en `n` y `MASK` y el resultado se asigna a `n`.  La constante de manifiesto `MASK` se define con una directiva de preprocesador [\#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## Vea también  
 [Operadores de asignación de C](../c-language/c-assignment-operators.md)
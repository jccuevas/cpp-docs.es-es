---
title: "Operadores unarios m&#225;s y de negaci&#243;n: + y - | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "+"
  - "-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "- (operador)"
  - "+ (operador)"
  - "+ (operador), operadores unarios"
  - "operador de negación"
  - "operadores unarios, plus"
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores unarios m&#225;s y de negaci&#243;n: + y -
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
  
```  
  
## \+ \(operador\)  
 El resultado del operador unario más \(**\+**\) es el valor de su operando.  El operando del operador unario más debe ser de tipo aritmético.  
  
 La promoción de entero se realiza en operandos enteros.  El tipo resultante es el tipo al que se promueve el operando.  Así, la expresión `+ch`, donde `ch` es de tipo `char`, produce el tipo `int`; el valor está sin modificar.  Vea [Promociones de entero](../misc/integral-promotions.md) para obtener más información sobre cómo se realiza la promoción.  
  
## \- \(operador\)  
 El operador de negación unario \(**–**\) genera el negativo de su operando.  El operando del operador de negación unario debe ser un tipo aritmético.  
  
 La promoción de entero se realiza en operandos enteros y el tipo resultante es el tipo al que se promueve el operando.  Vea [Promociones de entero](../misc/integral-promotions.md) para obtener más información sobre cómo se realiza la promoción.  
  
## Específicos de Microsoft  
 La negación unaria de cantidades sin signo se realiza restando el valor del operando de 2^n, donde n es el número de bits de un objeto del tipo sin signo especificado.  \(Microsoft C\+\+ se ejecuta en procesadores que utilizan aritmética de complemento de dos.  En los demás procesadores, el algoritmo de negación puede diferir\).  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
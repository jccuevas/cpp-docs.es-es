---
title: 'Operadores de negación y más unario: + y - | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1441337275ac07b0d1ba39e8bfa34e7165f87f82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="unary-plus-and-negation-operators--and--"></a>Operadores unarios más y de negación: + y -
## <a name="syntax"></a>Sintaxis  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
```  
  
## <a name="-operator"></a>+ (operador)  
 El resultado del operador unario más (**+**) es el valor de su operando. El operando del operador unario más debe ser de tipo aritmético.  
  
 La promoción de entero se realiza en operandos enteros. El tipo resultante es el tipo al que se promueve el operando. Así, la expresión `+ch`, donde `ch` es de tipo `char`, produce el tipo `int`; el valor está sin modificar. Vea [conversiones estándar](standard-conversions.md) para obtener más información sobre cómo se realiza la promoción.  
  
## <a name="--operator"></a>- (operador)  
 El operador unario de negación (**-**) genera el negativo de su operando. El operando del operador de negación unario debe ser un tipo aritmético.  
  
 La promoción de entero se realiza en operandos enteros y el tipo resultante es el tipo al que se promueve el operando. Vea [conversiones estándar](standard-conversions.md) para obtener más información acerca de cómo se realiza la promoción.  
  
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 La negación unaria de cantidades sin signo se realiza restando el valor del operando de 2^n, donde n es el número de bits de un objeto del tipo sin signo especificado.
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

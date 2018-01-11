---
title: Expresiones con operadores unarios | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44485f0c5749db36ececd2061955f9956cb49ece
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expressions-with-unary-operators"></a>Expresiones con operadores unarios
Los operadores unarios actúan solo sobre un operando en una expresión. Los operadores unarios son los siguientes:  
  
-   [Operador de direccionamiento indirecto (*)](../cpp/indirection-operator-star.md)  
  
-   [Operador Address-of (&)](../cpp/address-of-operator-amp.md)  
  
-   [Unario más (+), operador](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operador unario de negación (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operador lógico de negación (!)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [Operador complementario (~)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [Operador de incremento de prefijo (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operador de decremento de prefijo (-)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operador de conversión)](../cpp/cast-operator-parens.md)  
  
-   [operador sizeof](../cpp/sizeof-operator.md)  
  
-   [__uuidof (operador)](../cpp/uuidof-operator.md)  
  
-   [__alignof (operador)](../cpp/alignof-operator.md)  
  
-   [New (operador)](../cpp/new-operator-cpp.md)  
  
-   [Delete (operador)](../cpp/delete-operator-cpp.md)  
  
 Estos operadores tienen asociatividad de derecha a izquierda. Las expresiones unarias normalmente usan sintaxis que precede a una expresión de postfijo o primaria.  
  
 Estas son las posibles formas de expresiones unarias.  
  
-   *postfix-expression*  
  
-   `++`*expresión unaria*  
  
-   `--`*expresión unaria*  
  
-   *operador unario* *cast-expression*  
  
-   `sizeof`*expresión unaria*  
  
-   `sizeof(`*nombre-tipo*`)`  
  
-   `decltype(`*expresión*`)`  
  
-   *expresión de asignación*  
  
-   *expresión de desasignación*  
  
 Cualquier *postfix-expression* se considera un *expresión unaria*, y porque cualquier expresión principal se considera un *postfix-expression*, es cualquier expresiones primarias considera un *expresión unaria* también. Para obtener más información, consulte [expresiones de postfijo](../cpp/postfix-expressions.md) y [expresiones primarias](../cpp/primary-expressions.md).  
  
 A *operador unario* consta de uno o varios de los símbolos siguientes:`* & + - ! ~`  
  
 El *cast-expression* es una expresión unaria con una conversión opcional para cambiar el tipo. Para obtener más información, consulte [operador de conversión: ()](../cpp/cast-operator-parens.md).  
  
 Un *expresión* puede ser cualquier expresión. Para obtener más información, consulte [expresiones](../cpp/expressions-cpp.md).  
  
 El *expresión de asignación* hace referencia a la `new` operador. El *desasignación-expression* hace referencia a la `delete` operador. Para obtener más información, vea los vínculos anteriores en este tema.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de expresiones](../cpp/types-of-expressions.md)
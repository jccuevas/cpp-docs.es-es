---
title: "Expresiones con operadores unarios | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "expresiones [C++], operadores"
  - "expresiones [C++], operadores unarios"
  - "operadores unarios, expresiones con"
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Expresiones con operadores unarios
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores unarios actúan solo sobre un operando en una expresión.  Los operadores unarios son los siguientes:  
  
-   [Operador de direccionamiento indirecto \(\*\)](../cpp/indirection-operator-star.md)  
  
-   [Operador address\-of \(&\)](../cpp/address-of-operator-amp.md)  
  
-   [Operador unario más \(\+\)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operador unario de negación \(–\)](../misc/unary-negation-operator.md)  
  
-   [Operador lógico de negación \(\!\)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [Operador de complemento a uno \(~\)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [Operador de incremento de prefijo \(\+\+\)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operador de decremento de prefijo \(––\)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operador de conversión \(\)](../cpp/cast-operator-parens.md)  
  
-   [Operador sizeof](../cpp/sizeof-operator.md)  
  
-   [Operador \_\_uuidof](../cpp/uuidof-operator.md)  
  
-   [Operador \_\_alignof](../cpp/alignof-operator.md)  
  
-   [Operador new](../cpp/new-operator-cpp.md)  
  
-   [Operador delete](../cpp/delete-operator-cpp.md)  
  
 Estos operadores tienen asociatividad de derecha a izquierda.  Las expresiones unarias normalmente usan sintaxis que precede a una expresión de postfijo o primaria.  
  
 Estas son las posibles formas de expresiones unarias.  
  
-   *postfix\-expression*  
  
-   `++` *unary\-expression*  
  
-   `––` *unary\-expression*  
  
-   *unary\-operator* *cast\-expression*  
  
-   `sizeof` *unary\-expression*  
  
-   `sizeof(` *type\-name* `)`  
  
-   `decltype(` *expression* `)`  
  
-   *allocation\-expression*  
  
-   *deallocation\-expression*  
  
 Cualquier *postfix\-expression* se considera *unary\-expression* y, dado que cualquier expresión primaria se considera *postfix\-expression*, cualquier expresión primaria se considera *unary\-expression* también.  Para obtener más información, vea [Expresiones de sufijo](../cpp/postfix-expressions.md) y [Expresiones primarias](../cpp/primary-expressions.md).  
  
 *unary\-operator* consta de uno o más de los símbolos siguientes: `* &` `+` `–` `!` `~`  
  
 *cast\-expression* es una expresión unaria con una conversión opcional para cambiar el tipo.  Para obtener más información, vea [Operador de conversión: \(\)](../cpp/cast-operator-parens.md).  
  
 *expression* puede ser cualquier expresión.  Para obtener más información, vea [Expresiones](../cpp/expressions-cpp.md).  
  
 *allocation\-expression* hace referencia al operador `new`.  *deallocation\-expression* hace referencia al operador `delete`.  Para obtener más información, vea los vínculos anteriores en este tema.  
  
## Vea también  
 [Tipos de expresiones](../cpp/types-of-expressions.md)
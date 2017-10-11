---
title: Los operadores integrados de C++, prioridad y asociatividad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6c45b0d3ff2aaee6763b73949727dcde5ee744bc
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Los operadores integrados de C++, prioridad y asociatividad
El lenguaje C++ incluye todos los operadores de C y agrega varios operadores nuevos. Los operadores especifican una evaluación que se realizará en uno o más operandos.  
  
 La prioridad de los operadores especifica el orden en que se realizan las operaciones en las expresiones que contienen más de un operador. La asociatividad de los operadores especifica si, en una expresión que contiene varios operadores con la misma prioridad, un operando se agrupa con el de su izquierda o con el de su derecha. La tabla siguiente muestra la prioridad y la asociatividad de los operadores de C++ (de mayor a menor prioridad). Los operadores que tienen el mismo número de prioridad tienen la misma prioridad, a menos que se fuerce otra relación explícitamente mediante paréntesis.  
  
### <a name="c-operator-precedence-and-associativity"></a>Prioridad y asociatividad de los operadores de C++  
  
|Descripción del operador|Operador|  
|--------------------------|--------------|  
|`Group 1 precedence, no associativity`|  
|[Resolución de ámbito](../cpp/scope-resolution-operator.md)|`::`|  
|`Group 2 precedence, left to right associativity`|  
|[Selección de miembro (objeto o puntero)](../cpp/member-access-operators-dot-and.md)|`. or ->`|  
|[Subíndice de matriz](../cpp/subscript-operator.md)|`[ ]`|  
|[Llamada de función](../cpp/function-call-operator-parens.md)|`( )`|  
|[Incremento de postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[Decremento de postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`--`|  
|[Nombre de tipo](../cpp/typeid-operator.md)|`typeid( )`|  
|[Conversión de tipo de constante](../cpp/const-cast-operator.md)|`const_cast`|  
|[Conversión de tipos dinámica](../cpp/dynamic-cast-operator.md)|`dynamic_cast`|  
|[Conversión de tipos reinterpretada](../cpp/reinterpret-cast-operator.md)|`reinterpret_cast`|  
|[Conversión de tipos estática](../cpp/static-cast-operator.md)|`static_cast`|  
|`Group 3 precedence, right to left associativity`|  
|[Tamaño de objeto o tipo](../cpp/sizeof-operator.md)|`sizeof`|  
|[Incremento de prefijo](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[Decremento de prefijo](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|`--`|  
|[Complemento de uno](../cpp/one-s-complement-operator-tilde.md)|`~`|  
|[Not lógico](../cpp/logical-negation-operator-exclpt.md)|`!`|  
|[Negación unaria](../cpp/unary-plus-and-negation-operators-plus-and.md)|`-`|  
|[Unario más](../cpp/unary-plus-and-negation-operators-plus-and.md)|`+`|  
|[Dirección de](../cpp/lvalue-reference-declarator-amp.md)|`&`|  
|[Direccionamiento indirecto](../cpp/indirection-operator-star.md)|`*`|  
|[Crear objeto](../cpp/new-operator-cpp.md)|`new`|  
|[Destruir objeto](../cpp/delete-operator-cpp.md)|`delete`|  
|[Conversión de tipos](../cpp/cast-operator-parens.md)|`Cast: ()`|  
|`Group 4 precedence, left to right associativity`|  
|[Puntero a miembro (objetos o punteros)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|`.* or ->*`|  
|`Group 5 precedence, left to right associativity`|  
|[Multiplicación](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`*`|  
|[División](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`/`|  
|[Módulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`%`|  
|`Group 6 precedence, left to right associativity`|  
|[Adición](../cpp/additive-operators-plus-and.md)|`+`|  
|[Resta](../cpp/additive-operators-plus-and.md)|`-`|  
|`Group 7 precedence, left to right associativity`|  
|[Desplazamiento a la izquierda](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|`<<`|  
|[Desplazamiento a la derecha](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|`>>`|  
|`Group 8 precedence, left to right associativity`|  
|[Menor que](../cpp/relational-operators-equal-and-equal.md)|`<`|  
|[Mayor que](../cpp/relational-operators-equal-and-equal.md)|`>`|  
|[Menor o igual que](../cpp/relational-operators-equal-and-equal.md)|`<=`|  
|[Mayor o igual que](../cpp/relational-operators-equal-and-equal.md)|`>=`|  
|`Group 9 precedence, left to right associativity`|  
|[Igualdad](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|`==`|  
|[Desigualdad](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|`!=`|  
|`Group 10 precedence left to right associativity`|  
|[AND bit a bit](../cpp/bitwise-and-operator-amp.md)|`&`|  
|`Group 11 precedence, left to right associativity`|  
|[Bit a bit OR exclusivo](../cpp/bitwise-exclusive-or-operator-hat.md)|`^`|  
|`Group 12 precedence, left to right associativity`|  
|[Bit a bit OR inclusivo](../cpp/bitwise-inclusive-or-operator-pipe.md)|`&#124;`|  
|`Group 13 precedence, left to right associativity`|  
|[AND lógico](../cpp/logical-and-operator-amp-amp.md)|`&&`|  
|`Group 14 precedence, left to right associativity`|  
|[OR lógico](../cpp/logical-or-operator-pipe-pipe.md)|`&#124;&#124;`|  
|`Group 15 precedence, right to left associativity`|  
|[Condicional](../cpp/conditional-operator-q.md)|`? :`|  
|`Group 16 precedence, right to left associativity`|  
|[Asignación](../cpp/assignment-operators.md)|`=`|  
|[Asignación de multiplicación](../cpp/assignment-operators.md)|`*=`|  
|[Asignación y división](../cpp/assignment-operators.md)|`/=`|  
|[Asignación y módulo](../cpp/assignment-operators.md)|`%=`|  
|[Asignación de suma](../cpp/assignment-operators.md)|`+=`|  
|[Asignación y resta](../cpp/assignment-operators.md)|`-=`|  
|[Asignación de desplazamiento a la izquierda](../cpp/assignment-operators.md)|`<<=`|  
|[Asignación de desplazamiento a la derecha](../cpp/assignment-operators.md)|`>>=`|  
|[Asignación AND bit a bit](../cpp/assignment-operators.md)|`&=`|  
|[Bit a bit asignación y OR inclusiva](../cpp/assignment-operators.md)|`&#124;=`|  
|[Bit a bit asignación y OR exclusivo](../cpp/assignment-operators.md)|`^=`|  
|`Group 17 precedence, right to left associativity`|  
|[expresión throw](../cpp/try-throw-and-catch-statements-cpp.md)|`throw`|  
|`Group 18 precedence, left to right associativity`|  
|[Coma](../cpp/comma-operator.md)|`,`|  
  
## <a name="see-also"></a>Vea también  
[Sobrecarga de operadores](operator-overloading.md)




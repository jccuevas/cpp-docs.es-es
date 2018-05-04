---
title: Los operadores integrados de C++, prioridad y asociatividad | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4d2bb339d4147e6ea82c713d83a046e0e9780bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Los operadores integrados de C++, prioridad y asociatividad

El lenguaje C++ incluye todos los operadores de C y agrega varios operadores nuevos. Los operadores especifican una evaluación que se realizará en uno o más operandos.

Operador *prioridad* especifica el orden de las operaciones en las expresiones que contienen más de un operador. Operador *asociatividad* especifica si, en una expresión que contiene varios operadores con la misma prioridad, un operando se agrupa con el de su izquierda o el de su derecha. La tabla siguiente muestra la prioridad y la asociatividad de los operadores de C++ (de mayor a menor prioridad). Los operadores que tienen el mismo número de prioridad tienen la misma prioridad, a menos que se fuerce otra relación explícitamente mediante paréntesis.

### <a name="c-operator-precedence-and-associativity"></a>Prioridad y asociatividad de los operadores de C++

|Descripción del operador|Operador|
|--------------------------|--------------|
|**Grupo 1 prioridad, ninguna capacidad de asociación**|
|[Resolución de ámbito](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Prioridad de grupo 2, de izquierda a derecha asociatividad**|
|[Selección de miembro (objeto o puntero)](../cpp/member-access-operators-dot-and.md)|[. o ->](../cpp/member-access-operators-dot-and.md)|
|[Subíndice de matriz](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Llamada de función](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Incremento de postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Decremento de postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Nombre de tipo](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Conversión de tipo de constante](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Conversión de tipos dinámica](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Conversión de tipos reinterpretada](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Conversión de tipos estática](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Prioridad de grupo 3, de derecha a izquierda asociatividad**|
|[Tamaño de objeto o tipo](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Incremento de prefijo](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Decremento de prefijo](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Complemento de uno](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Not lógico](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[Negación unaria](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Unario más](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Dirección de](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Direccionamiento indirecto](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Crear objeto](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[Destruir objeto](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Conversión de tipos](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Prioridad de grupo 4, de izquierda a derecha asociatividad**|
|[Puntero a miembro (objetos o punteros)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; o ->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Prioridad de 5, de izquierda a derecha asociatividad de grupo**|
|[Multiplicación](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[División](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Módulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Prioridad de grupo 6, de izquierda a derecha asociatividad**|
|[Suma](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Resta](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Prioridad 7, de izquierda a derecha asociatividad de grupo**|
|[Desplazamiento a la izquierda](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Desplazamiento a la derecha](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Prioridad de 8, de izquierda a derecha asociatividad de grupo**|
|[Menor que](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Mayor que](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Menor o igual que](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Mayor o igual que](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Prioridad de 9, de izquierda a derecha asociatividad de grupo**|
|[Igualdad](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Desigualdad](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Prioridad de grupo 10 de izquierda a derecha asociatividad**|
|[AND bit a bit](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Prioridad de grupo 11, de izquierda a derecha asociatividad**|
|[Bit a bit OR exclusivo](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Prioridad de 12, de izquierda a derecha asociatividad de grupo**|
|[Bit a bit OR inclusivo](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Prioridad de 13, de izquierda a derecha asociatividad de grupo**|
|[AND lógico](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Prioridad de grupo 14, de izquierda a derecha asociatividad**|
|[OR lógico](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Prioridad de 15, de derecha a izquierda asociatividad de grupo**|
|[Condicional](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Prioridad de 16, de derecha a izquierda asociatividad de grupo**|
|[Asignación](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Asignación de multiplicación](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Asignación y división](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Asignación y módulo](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Asignación de suma](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Asignación y resta](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Asignación de desplazamiento a la izquierda](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Asignación de desplazamiento a la derecha](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Asignación AND bit a bit](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Bit a bit asignación y OR inclusiva](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Bit a bit asignación y OR exclusivo](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Prioridad de 17, de derecha a izquierda asociatividad de grupo**|
|[expresión throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Prioridad de 18, de izquierda a derecha asociatividad de grupo**|
|[Coma](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Vea también

[Sobrecarga de operadores](operator-overloading.md)



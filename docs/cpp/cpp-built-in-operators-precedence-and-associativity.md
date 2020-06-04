---
title: C++Operadores integrados, precedencia y asociatividad
ms.date: 11/04/2016
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
ms.openlocfilehash: 36e7ce77e24366be10b75f5bb4f8830363594301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180412"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++Operadores integrados, precedencia y asociatividad

El lenguaje C++ incluye todos los operadores de C y agrega varios operadores nuevos. Los operadores especifican una evaluación que se realizará en uno o más operandos.

La *precedencia* de operadores especifica el orden de las operaciones en expresiones que contienen más de un operador. La *asociatividad* del operador especifica si, en una expresión que contiene varios operadores con la misma prioridad, un operando se agrupa con el que se encuentra a la izquierda o a la derecha. La tabla siguiente muestra la prioridad y la asociatividad de los operadores de C++ (de mayor a menor prioridad). Los operadores que tienen el mismo número de prioridad tienen la misma prioridad, a menos que se fuerce otra relación explícitamente mediante paréntesis.

### <a name="c-operator-precedence-and-associativity"></a>Prioridad y asociatividad de los operadores de C++

|Descripción del operador|Operator|
|--------------------------|--------------|
|**Precedencia de grupo 1, sin asociatividad**|
|[Resolución de ámbito](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Precedencia de grupo 2, asociatividad de izquierda a derecha**|
|[Selección de miembro (objeto o puntero)](../cpp/member-access-operators-dot-and.md)|[. o->](../cpp/member-access-operators-dot-and.md)|
|[Subíndice de matriz](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Llamada de función](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Incremento de postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Decremento de postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Nombre de tipo](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Conversión de tipos constante](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Conversión dinámica de tipos](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Conversión de tipos reinterpretada](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Conversión de tipos estáticos](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Precedencia de grupo 3, asociatividad de derecha a izquierda**|
|[Tamaño del objeto o tipo](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Incremento de prefijo](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Decremento de prefijo](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Complemento de uno](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Not lógico](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[Negación unaria](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Signo más unario](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Dirección de](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Direccionamiento indirecto](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Crear objeto](../cpp/new-operator-cpp.md)|[nuevo](../cpp/new-operator-cpp.md)|
|[Destruir objeto](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Cast](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Precedencia de grupo 4, asociatividad de izquierda a derecha**|
|[Puntero a miembro (objetos o punteros)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; o->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Precedencia de grupo 5, asociatividad de izquierda a derecha**|
|[Multiplicación](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[División](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Módulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Precedencia de grupo 6, asociatividad de izquierda a derecha**|
|[Suma](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Resta](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Precedencia de grupo 7, asociatividad de izquierda a derecha**|
|[Desplazamiento a la izquierda](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Desplazamiento a la derecha](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Precedencia de grupo 8, asociatividad de izquierda a derecha**|
|[Menor que](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Mayor que](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Menor o igual que](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Mayor o igual que](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Precedencia de grupo 9, asociatividad de izquierda a derecha**|
|[Igualdad](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Desigualdad](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Precedencia de grupo 10 de izquierda a derecha**|
|[AND bit a bit](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Precedencia de grupo 11, asociatividad de izquierda a derecha**|
|[Or exclusivo bit a bit](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Precedencia de grupo 12, asociatividad de izquierda a derecha**|
|[Or inclusivo bit a bit](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Precedencia de grupo 13, asociatividad de izquierda a derecha**|
|[Y lógico](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Precedencia de grupo 14, asociatividad de izquierda a derecha**|
|[O lógico](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Precedencia de grupo 15, asociatividad de derecha a izquierda**|
|[Instrucción](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Precedencia de grupo 16, asociatividad de derecha a izquierda**|
|[Asignación](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Asignación de multiplicación](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Asignación de división](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Asignación de módulo](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Asignación de suma](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Asignación de resta](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Asignación de desplazamiento a la izquierda](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Asignación de desplazamiento a la derecha](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Asignación and bit a bit](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Asignación or inclusivo bit a bit](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Asignación OR exclusiva bit a bit](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Precedencia de grupo 17, asociatividad de derecha a izquierda**|
|[expresión Throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Precedencia de grupo 18, asociatividad de izquierda a derecha**|
|[Coma](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Consulte también

[Sobrecarga de operadores](operator-overloading.md)

---
title: Expresiones con operadores unarios
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 26aad64e5b9c7a496c2e6bb131b82740c06abe07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188979"
---
# <a name="expressions-with-unary-operators"></a>Expresiones con operadores unarios

Los operadores unarios actúan solo sobre un operando en una expresión. Los operadores unarios son los siguientes:

- [Operador de direccionamiento indirecto (*)](../cpp/indirection-operator-star.md)

- [Operador Address-of (&)](../cpp/address-of-operator-amp.md)

- [Operador unario más (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Operador unario de negación (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Operador lógico de negación (!)](../cpp/logical-negation-operator-exclpt.md)

- [Operador de complemento de uno (~)](../cpp/one-s-complement-operator-tilde.md)

- [Operador de incremento de prefijo (+ +)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Operador de decremento de prefijo (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Operador de conversión ()](../cpp/cast-operator-parens.md)

- [sizeof (operador)](../cpp/sizeof-operator.md)

- [__uuidof (operador)](../cpp/uuidof-operator.md)

- [__alignof (operador)](../cpp/alignof-operator.md)

- [New (operador)](../cpp/new-operator-cpp.md)

- [Delete (operador)](../cpp/delete-operator-cpp.md)

Estos operadores tienen asociatividad de derecha a izquierda. Las expresiones unarias normalmente usan sintaxis que precede a una expresión de postfijo o primaria.

Estas son las posibles formas de expresiones unarias.

- *postfix-expression*

- `++` *expresión unaria*

- `--` *expresión unaria*

- *unario-* *conversión de operador-expresión*

- **sizeof** *(expresión unaria)*

- `sizeof(` *nombre de tipo* `)`

- `decltype(` *expresión* `)`

- *asignación: expresión*

- *desasignación: expresión*

Cualquier *expresión de postfijo* se considera una *expresión unaria*, y dado que cualquier expresión principal se considera una *expresión de postfijo*, cualquier expresión principal se considera también una *expresión unaria* . Para obtener más información, vea [expresiones de postfijo](../cpp/postfix-expressions.md) y [expresiones primarias](../cpp/primary-expressions.md).

Un *operador unario* se compone de uno o varios de los siguientes símbolos: `* & + - ! ~`

*Cast-Expression* es una expresión unaria con una conversión opcional para cambiar el tipo. Para obtener más información, vea [operador de conversión: ()](../cpp/cast-operator-parens.md).

Una *expresión* puede ser cualquier expresión. Para obtener más información, vea [expresiones](../cpp/expressions-cpp.md).

La *expresión de asignación* hace referencia al **nuevo** operador. La *deasignación-expresión* hace referencia al operador **Delete** . Para obtener más información, vea los vínculos anteriores en este tema.

## <a name="see-also"></a>Consulte también

[Tipos de expresiones](../cpp/types-of-expressions.md)

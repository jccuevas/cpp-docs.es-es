---
title: Sobrecargar operadores unarios
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 60444ee3c55df39e6b7820ff9b9d7ad81017b0da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188498"
---
# <a name="overloading-unary-operators"></a>Sobrecargar operadores unarios

Los operadores unarios que se pueden sobrecargar son los siguientes:

1. `!` ([Not lógico](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([dirección de](../cpp/address-of-operator-amp.md))

1. `~` ([complemento de uno](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([desreferencia de puntero](../cpp/indirection-operator-star.md))

1. `+` ([más unario](../cpp/additive-operators-plus-and.md))

1. `-` ([negación unaria](../cpp/additive-operators-plus-and.md))

1. `++` ([incremento](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([decremento](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. operadores de conversión

Los operadores de incremento y decremento de postfijo (`++` y `--`) se tratan por separado en [incremento y decremento](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Los operadores de conversión también se tratan en un tema independiente; vea [conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md).

Las reglas siguientes son ciertas para todos los demás operadores unarios. Para declarar una función de operador unario como miembro no estático, debe declararla de la forma siguiente:

> *RET-Type* **operador** *OP* **()**

donde *RET-Type* es el tipo de valor devuelto y *OP* es uno de los operadores enumerados en la tabla anterior.

Para declarar una función de operador unario como función global, debe declararla de la forma siguiente:

> *RET-Type* **operador** *OP* **(** *arg* **)**

donde *RET-Type* y *OP* son como se describen para las funciones de operador de miembro y *arg* es un argumento de tipo de clase en el que se va a operar.

> [!NOTE]
>  No hay restricciones en los tipos de valor devuelto de los operadores unarios. Por ejemplo, tiene sentido que el operador NOT lógico (`!`) devuelva un valor entero, pero esto no siempre sucede así.

## <a name="see-also"></a>Consulte también

[Sobrecarga de operadores](../cpp/operator-overloading.md)

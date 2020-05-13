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
ms.openlocfilehash: 971ef08c5e79f851c502ea872c541517065797c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372027"
---
# <a name="overloading-unary-operators"></a>Sobrecargar operadores unarios

Los operadores unarios que se pueden sobrecargar son los siguientes:

1. `!`([NO lógico](../cpp/logical-negation-operator-exclpt.md))

1. `&`([dirección de](../cpp/address-of-operator-amp.md))

1. `~`(complemento[de uno)](../cpp/one-s-complement-operator-tilde.md)

1. `*`([desreferencia del puntero](../cpp/indirection-operator-star.md))

1. `+`([unario más](../cpp/additive-operators-plus-and.md))

1. `-`([negación unaria](../cpp/additive-operators-plus-and.md))

1. `++`([incremento](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([disminución](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. operadores de conversión

Los operadores de incremento y`++` `--`decremento de postfijo ( y ) se tratan por separado en [Incremento y Decremento](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Los operadores de conversión también se describen en un tema independiente; Consulte [Conversiones de tipo definidas por el usuario](../cpp/user-defined-type-conversions-cpp.md).

Las reglas siguientes son ciertas para todos los demás operadores unarios. Para declarar una función de operador unario como miembro no estático, debe declararla de la forma siguiente:

> **operador** de *tipo ret* *op* **()**

donde *ret-type* es el tipo de valor devuelto y *op* es uno de los operadores enumerados en la tabla anterior.

Para declarar una función de operador unario como función global, debe declararla de la forma siguiente:

> **operador** de *tipo ret* *op* **(** *arg* **)**

donde *ret-type* y *op* son como se describe para las funciones de operador miembro y el *arg* es un argumento de tipo de clase en el que operar.

> [!NOTE]
> No hay restricciones en los tipos de valor devuelto de los operadores unarios. Por ejemplo, tiene sentido que el operador NOT lógico (`!`) devuelva un valor entero, pero esto no siempre sucede así.

## <a name="see-also"></a>Consulte también

[Sobrecarga del operador](../cpp/operator-overloading.md)

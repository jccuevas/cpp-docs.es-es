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
ms.openlocfilehash: 802380bad59534e8402020142e394b3948032476
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377236"
---
# <a name="overloading-unary-operators"></a>Sobrecargar operadores unarios

Los operadores unarios que se pueden sobrecargar son los siguientes:

1. `!` ([NOT lógico](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([address-of](../cpp/address-of-operator-amp.md))

1. `~` ([complementario](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([desreferencia de puntero](../cpp/indirection-operator-star.md))

1. `+` ([suma unaria](../cpp/additive-operators-plus-and.md))

1. `-` ([negación unaria](../cpp/additive-operators-plus-and.md))

1. `++` ([increment](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([decremento](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. operadores de conversión

El incremento de postfijo y operadores de decremento (`++` y `--`) se tratan por separado en [incremento y decremento](../cpp/increment-and-decrement-operator-overloading-cpp.md).

También se describen los operadores de conversión en un tema independiente; consulte [conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md).

Las reglas siguientes son ciertas para todos los demás operadores unarios. Para declarar una función de operador unario como miembro no estático, debe declararla de la forma siguiente:

> *ret-type* **operator** *op* **()**

donde *ret-type* es el tipo de valor devuelto y *op* es uno de los operadores enumerados en la tabla anterior.

Para declarar una función de operador unario como función global, debe declararla de la forma siguiente:

> *ret-type* **operator** *op* **(** *arg* **)**

donde *ret-type* y *op* son descrito para las funciones de operador de miembro y el *arg* es un argumento de tipo de clase en el que se va a operar.

> [!NOTE]
>  No hay restricciones en los tipos de valor devuelto de los operadores unarios. Por ejemplo, tiene sentido que el operador NOT lógico (`!`) devuelva un valor entero, pero esto no siempre sucede así.

## <a name="see-also"></a>Vea también

[Sobrecarga de operadores](../cpp/operator-overloading.md)
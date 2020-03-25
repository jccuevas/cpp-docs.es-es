---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: db246cda79c778f37c5afbfda4a68c191c474e12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190500"
---
# <a name="bool-c"></a>bool (C++)

Esta palabra clave es un tipo integrado. Una variable de este tipo puede tener valores [true](../cpp/true-cpp.md) y [false](../cpp/false-cpp.md). Las expresiones condicionales tienen el tipo **bool** y, por tanto, tienen valores de tipo **bool**. Por ejemplo, `i!=0` ahora tiene TRUE o FALSE según el valor de `i`.

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): el operando de un operador de incremento o decremento de prefijo o de prefijo no puede ser de tipo **bool**. En otras palabras, dado una variable `b` de tipo **bool**, estas expresiones ya no se permiten:

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Los valores TRUE y FALSE tienen la relación siguiente:

```cpp
!false == true
!true == false
```

En la instrucción siguiente:

```cpp
if (condexpr1) statement1;
```

Si `condexpr1` es TRUE, se ejecuta siempre `statement1`; Si `condexpr1` es FALSE, nunca se ejecuta `statement1`.

Cuando se aplica un operador de **++** de sufijo o prefijo a una variable de tipo **bool**, la variable se establece en true.
**Visual Studio 2017 versión 15,3 y posterior**: Operator + + para **bool** se quitó del lenguaje y ya no se admite.

El operador de **--** de sufijo o prefijo no se puede aplicar a una variable de este tipo.

El tipo **bool** participa en promociones enteras. Un valor r de tipo **bool** se puede convertir en un valor r de tipo **int**, con false como cero y true como uno. Como un tipo distinto, **bool** participa en la resolución de sobrecarga.

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Tipos integrados](../cpp/fundamental-types-cpp.md)

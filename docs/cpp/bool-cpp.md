---
title: BOOL (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce07cfce4b7361486489c2f00c3e4b395c71e200
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058515"
---
# <a name="bool-c"></a>bool (C++)

Esta palabra clave es un tipo integrado. Una variable de este tipo puede tener valores [true](../cpp/true-cpp.md) y [false](../cpp/false-cpp.md). Las expresiones condicionales tienen el tipo **bool** y por lo que tienen valores de tipo **bool**. Por ejemplo, `i!=0` tiene ahora el verdadero o falso dependiendo del valor de `i`.

**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): el operando de un prefijo o postfijo de incremento o decremento operador no puede ser de tipo **bool**. En otras palabras, dada una variable `b` typu **bool**, ya no se permiten estas expresiones:

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

Si `condexpr1` es TRUE, `statement1` siempre se ejecuta; si `condexpr1` es FALSE, `statement1` nunca se ejecuta.

Cuando un prefijo o postfijo **++** operador se aplica a una variable de tipo **bool**, la variable se establece en TRUE.
**Visual Studio 2017 versión 15.3 y versiones posterior**: operator ++ para **bool** se ha quitado del lenguaje y ya no se admite.

El prefijo o postfijo **--** operador no se puede aplicar a una variable de este tipo.

El **bool** tipo participa en promociones de enteros. Un valor r del tipo **bool** puede convertirse en un valor r del tipo **int**, con cada vez FALSE cero y TRUE como uno. Como un tipo distinto, **bool** participa en la resolución de sobrecarga.

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Tipos fundamentales](../cpp/fundamental-types-cpp.md)
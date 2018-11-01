---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: 5cfc99f446499201a0f54c8e5b1dcc2d7152445c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488598"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>Sintaxis

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>Comentarios

Esta palabra clave es uno de los dos valores de una variable de tipo [bool](../cpp/bool-cpp.md) o una expresión condicional (una expresión condicional es ahora una expresión booleana true). Si `i` es de tipo **bool**, a continuación, la instrucción `i = true;` asigna **true** a `i`.

## <a name="example"></a>Ejemplo

```cpp
// bool_true.cpp
#include <stdio.h>
int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)
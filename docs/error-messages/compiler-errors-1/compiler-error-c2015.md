---
title: Error del compilador C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 83b78336d74037b9f9f52da8327479f506db1ffc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751079"
---
# <a name="compiler-error-c2015"></a>Error del compilador C2015

demasiados caracteres en la constante

Una constante de caracteres contiene más de dos caracteres. El límite es un carácter para las constantes de caracteres estándar y dos caracteres para las constantes de caracteres largos.

Una secuencia de escape, como \t, se convierte en un único carácter.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2015:

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>Ejemplo

C2015 también se puede producir cuando se usa una extensión de Microsoft, las constantes de caracteres se convierten en enteros.  En el ejemplo siguiente se genera C2015:

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```

---
title: Error del compilador C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: d761dfde26cce9c99ccd4c3e6fd86ae1d6e16ddc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573282"
---
# <a name="compiler-error-c2015"></a>Error del compilador C2015

demasiados caracteres en la constante

Una constante de caracteres contiene más de dos caracteres. El límite es un carácter para las constantes de caracteres estándar y dos caracteres para las constantes de cadenas largas de caracteres.

Una secuencia de escape, por ejemplo, \t, se convierte en un único carácter.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2015:

```
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>Ejemplo

C2015 también puede producirse al usar una extensión de Microsoft, las constantes de caracteres que se convierten en enteros.  El ejemplo siguiente genera C2015:

```
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
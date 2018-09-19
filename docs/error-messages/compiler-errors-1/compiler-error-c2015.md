---
title: Error del compilador C2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fb9c3ba86224906f749088b96e5daae364d99e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076052"
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
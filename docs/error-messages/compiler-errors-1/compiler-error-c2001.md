---
title: Error del compilador C2001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71048a706678e4d9e6906972ebf148748927e829
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088247"
---
# <a name="compiler-error-c2001"></a>Error del compilador C2001

nueva línea en constante

Una constante de cadena no se puede continuar en una segunda línea a menos que realice lo siguiente:

- La primera línea con una barra diagonal inversa final.

- La cadena en la primera línea con comillas dobles de cierre y abra la cadena en la línea siguiente con otras comillas dobles.

La primera línea con \n final no es suficiente.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2001:

```
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

## <a name="example"></a>Ejemplo

Se incluyen espacios al principio de la línea siguiente después de un carácter de continuación de línea en la constante de cadena. Ninguno de los ejemplos anteriores incrustar un carácter de nueva línea en la constante de cadena. Puede insertar un carácter de nueva línea como se muestra aquí:

```
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```
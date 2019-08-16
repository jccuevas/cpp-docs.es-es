---
title: Error del compilador C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 03b54fe2373063c8c0f9905da93822928392998d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209028"
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
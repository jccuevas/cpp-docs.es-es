---
title: Error del compilador C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 2bf9bd322812764b2f63493d4b22b58d853a25fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756843"
---
# <a name="compiler-error-c2001"></a>Error del compilador C2001

nueva línea en constante

Una constante de cadena no puede continuar en una segunda línea a menos que haga lo siguiente:

- Finaliza la primera línea con una barra diagonal inversa.

- Cierre la cadena de la primera línea con comillas dobles y abra la cadena en la línea siguiente con otra comilla doble.

Finalizar la primera línea con \n no es suficiente.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2001:

```cpp
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

Se incluyen espacios al principio de la línea siguiente después de un carácter de continuación de línea en la constante de cadena. Ninguno de los ejemplos mostrados anteriormente inserta un carácter de nueva línea en la constante de cadena. Puede insertar un carácter de nueva línea como se muestra aquí:

```cpp
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

---
title: continue (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6fbc4af6a9a56f3406582ea9ba59f4d5759b88a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607485"
---
# <a name="continue-statement-c"></a>continue (Instrucción) (C++)

Fuerza la transferencia del control a la expresión de control de los más pequeño incluye [hacer](../cpp/do-while-statement-cpp.md), [para](../cpp/for-statement-cpp.md), o [mientras](../cpp/while-statement-cpp.md) bucle.

## <a name="syntax"></a>Sintaxis

```
continue;
```

## <a name="remarks"></a>Comentarios

No se ejecuta ninguna de las instrucciones restantes de la iteración actual. La siguiente iteración del bucle se determina del modo siguiente:

- En un **hacer** o **mientras** bucle, la siguiente iteración empieza evaluando la expresión de control de la **hacer** o **mientras** instrucción.

- En un **para** bucle (mediante la sintaxis `for`(`init-expr`; `cond-expr`; `loop-expr`)), el `loop-expr` cláusula se ejecuta. A continuación, se evalúa de nuevo la cláusula `cond-expr` y, en función del resultado, el bucle finaliza o se produce otra iteración.

El ejemplo siguiente se muestra cómo el **continuar** instrucción puede utilizarse para omitir secciones de código y comenzar la siguiente iteración de un bucle.

## <a name="example"></a>Ejemplo

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>Vea también

[Instrucciones de salto](../cpp/jump-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
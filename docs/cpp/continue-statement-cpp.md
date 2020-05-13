---
title: continue (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: b3790ecfde0af958b3244cfdaa61524ba78d6267
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180282"
---
# <a name="continue-statement-c"></a>continue (Instrucción) (C++)

Fuerza la transferencia de control a la expresión de control del bucle [de inclusión más](../cpp/do-while-statement-cpp.md)pequeño, [for](../cpp/for-statement-cpp.md)o [While](../cpp/while-statement-cpp.md) .

## <a name="syntax"></a>Sintaxis

```
continue;
```

## <a name="remarks"></a>Observaciones

No se ejecuta ninguna de las instrucciones restantes de la iteración actual. La siguiente iteración del bucle se determina del modo siguiente:

- En un bucle **do** o **While** , la siguiente iteración comienza reevaluando la expresión de control de la instrucción **do** o **While** .

- En un bucle **for** (mediante la sintaxis `for`(`init-expr`; `cond-expr`; `loop-expr`)), se ejecuta la cláusula `loop-expr`. A continuación, se evalúa de nuevo la cláusula `cond-expr` y, en función del resultado, el bucle finaliza o se produce otra iteración.

En el ejemplo siguiente se muestra cómo se puede usar la instrucción **continue** para omitir secciones de código e iniciar la siguiente iteración de un bucle.

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

## <a name="see-also"></a>Consulte también

[Instrucciones de salto](../cpp/jump-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)

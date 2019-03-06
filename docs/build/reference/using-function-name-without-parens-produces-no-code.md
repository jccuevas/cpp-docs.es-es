---
title: La utilización de un nombre de función sin () no genera código
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 50053244787d1ceafe4e60083e7e7353e337dbbe
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424904"
---
# <a name="using-function-name-without--produces-no-code"></a>La utilización de un nombre de función sin () no genera código

Cuando se usa un nombre de función declarado en el programa sin paréntesis, el compilador no genera código. Esto ocurre independientemente de si la función toma parámetros porque el compilador calcula la dirección de función; Sin embargo, dado que el operador de llamada de función "()" no está presente, se realiza ninguna llamada. El resultado es similar al siguiente:

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

En Visual C++, incluso con el nivel de advertencia 4, genera ningún resultado de diagnóstico. Se genera ninguna advertencia; no se genera ningún código.

El código de ejemplo siguiente se compila (con una advertencia) y vincula correctamente sin errores, pero no genera código en relación con `funcn( )`. Para que funcione correctamente, agregue el operador de llamada de función "()".

```
#include <stdio.h>
void funcn();

int main() {
   funcn;      /* missing function call operator;
                  call will fail.  Use funcn() */
   }

void funcn() {
   printf("\nHello World\n");
}
```

## <a name="see-also"></a>Vea también

[Optimizar el código](../../build/reference/optimizing-your-code.md)

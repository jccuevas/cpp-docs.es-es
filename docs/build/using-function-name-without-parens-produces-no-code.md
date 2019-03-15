---
title: La utilización de un nombre de función sin () no genera código
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827795"
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

[Optimizar el código](optimizing-your-code.md)

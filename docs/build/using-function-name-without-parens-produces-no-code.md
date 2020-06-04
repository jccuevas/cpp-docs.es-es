---
title: La utilización de un nombre de función sin () no genera código
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314603"
---
# <a name="using-function-name-without--produces-no-code"></a>La utilización de un nombre de función sin () no genera código

Cuando se usa un nombre de función declarado en el programa sin paréntesis, el compilador no genera código. Esto se produce independientemente de si la función toma o no parámetros, porque el compilador calcula la dirección de la función. Sin embargo, como el operador de llamada de función "()" no está presente, no se realiza ninguna llamada. El resultado es similar al siguiente:

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

En Visual C++, no se genera ningún resultado de diagnóstico ni siquiera con el nivel de advertencia 4. No se genera ninguna advertencia ni se devuelve código.

El código de ejemplo siguiente se compila (con una advertencia) y se vincula correctamente sin errores, pero no genera código en referencia a `funcn( )`. Para que esto funcione correctamente, agregue el operador de llamada de función "()".

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

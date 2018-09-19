---
title: Uso de nombre de función sin () No genera código | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ca43386c9ef46f526538781a91fd1a81ade537
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710585"
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
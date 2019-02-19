---
title: break (Instrucción) (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: b38ff6c535c142bd15ea09a4d7c80010c3fff31f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149822"
---
# <a name="break-statement-c"></a>break (Instrucción) (C)

La instrucción `break` finaliza la ejecución de la instrucción `do`, `for`, `switch` o `while` más próxima que la incluya. El control pasa a la instrucción que hay a continuación de la instrucción finalizada.

## <a name="syntax"></a>Sintaxis

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**

La instrucción `break` se usa con frecuencia para finalizar el procesamiento de un caso concreto en una instrucción `switch`. Si no existe una instrucción iterativa o una instrucción `switch` incluyente, se genera un error.

Dentro de las instrucciones anidadas, la instrucción `break` finaliza solo la instrucción `do`, `for`, `switch` o `while` que la incluye de forma inmediata. Puede usar una instrucción `return` o `goto` para transferir el control fuera de la estructura anidada.

En este ejemplo se ilustra la instrucción `break`:

```
#include <stdio.h>
int main() {
   char c;
   for(;;) {
      printf_s( "\nPress any key, Q to quit: " );

      // Convert to character value
      scanf_s("%c", &c);
      if (c == 'Q')
          break;
   }
} // Loop exits only when 'Q' is pressed
```

## <a name="see-also"></a>Vea también

[break (Instrucción)](../cpp/break-statement-cpp.md)

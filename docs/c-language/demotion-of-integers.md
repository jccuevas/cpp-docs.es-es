---
title: Disminución de enteros
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: edfb8f03094c10cf0cf33b0eb799d5d822ac017d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234410"
---
# <a name="demotion-of-integers"></a>Disminución de enteros

**ANSI 3.2.1.2** El resultado de convertir un entero en un entero menor con signo o el resultado de convertir un entero sin signo en un entero con signo de igual longitud, si no se puede representar el valor

Cuando un entero **long** se convierte en un entero **short**, o cuando un entero **short** se convierte en un `char`, se conservan los bytes menos significativos.

Por ejemplo, esta línea

```
short x = (short)0x12345678L;
```

asigna el valor 0x5678 a `x`, y esta línea

```
char y = (char)0x1234;
```

asigna el valor 0x34 a `y`.

Cuando las variables con signo se convierten en variables sin signo, y viceversa, los patrones de bits permanecen iguales. Por ejemplo, la conversión de -2 (0xFE) en un valor sin signo produce 254 (también 0xFE).

## <a name="see-also"></a>Vea también

[Enteros](../c-language/integers.md)

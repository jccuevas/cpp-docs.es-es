---
title: Operaciones bit a bit con signo
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: 43f65fd5d1ea14ef5e15f18d9c8516ccf5fb1e08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158324"
---
# <a name="signed-bitwise-operations"></a>Operaciones bit a bit con signo

**ANSI 3.3** Resultados de operaciones bit a bit en enteros con signo

Las operaciones bit a bit en enteros con signo funcionan igual que las operaciones bit a bit en enteros sin signo. Por ejemplo, `-16 & 99` puede expresarse en formato binario como

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

El resultado de AND bit a bit es 96.

## <a name="see-also"></a>Vea también

[Enteros](../c-language/integers.md)

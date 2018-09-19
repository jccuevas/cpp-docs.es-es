---
title: Operaciones bit a bit con signo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184fd5a0e6c12cb58e9fed759459e7b8172896f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038302"
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
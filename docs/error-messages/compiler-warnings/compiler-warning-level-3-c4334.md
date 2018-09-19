---
title: Compilador advertencia (nivel 3) C4334 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7bb16ea38b2c2112c12c561398341a7d1adbfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044020"
---
# <a name="compiler-warning-level-3-c4334"></a>Advertencia del compilador (nivel 3) C4334

'operador': el resultado del desplazamiento de 32 bits se convierte implícitamente en 64 bits (era quería un desplazamiento de 64 bits?)

El resultado del desplazamiento de 32 bits se convirtió implícitamente en 64 bits y el compilador supuso que estaba previsto un desplazamiento de 64 bits.  Para resolver esta advertencia, utilice el desplazamiento de 64 bits, o convertir explícitamente el resultado a 64 bits.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4334.

```
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```
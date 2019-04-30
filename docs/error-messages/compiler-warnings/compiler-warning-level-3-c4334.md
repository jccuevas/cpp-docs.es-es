---
title: Advertencia del compilador (nivel 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 55512bf28c8c20512d0d245810d3e5c1fec36939
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402039"
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
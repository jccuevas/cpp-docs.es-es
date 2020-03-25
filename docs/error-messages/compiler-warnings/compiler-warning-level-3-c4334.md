---
title: Advertencia del compilador (nivel 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 38b93c83f822bc5b856a46f0dd62ea275d2bf207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198723"
---
# <a name="compiler-warning-level-3-c4334"></a>Advertencia del compilador (nivel 3) C4334

' operador ': el resultado del desplazamiento de 32 bits se convierte implícitamente a 64 bits (¿está previsto el desplazamiento de 64 bits?)

El resultado del desplazamiento de 32 bits se convirtió implícitamente en 64 bits, y el compilador sospecha que se pretendía un desplazamiento de 64 bits.  Para resolver esta advertencia, use el desplazamiento de 64 bits o convierta explícitamente el resultado del desplazamiento a 64 bits.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4334.

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```

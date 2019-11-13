---
title: ADVERTENCIA del compilador (nivel 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: ebebfe9994be3dd136e3924cb2aea60c0c901926
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051632"
---
# <a name="compiler-warning-level-3-c4334"></a>ADVERTENCIA del compilador (nivel 3) C4334

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
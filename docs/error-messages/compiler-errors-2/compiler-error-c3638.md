---
title: Error del compilador C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 8b1ef7f4cb38653f0ccdfae5684eb2907a735af7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486897"
---
# <a name="compiler-error-c3638"></a>Error del compilador C3638

'operador': no se puede redefinir la conversión boxing estándar y los operadores de conversión unboxing

El compilador define un operador de conversión para cada clase administrada para admitir la conversión boxing implícita. Este operador no se puede redefinir.

Para obtener más información, consulte [conversión Boxing implícita](../../windows/boxing-cpp-component-extensions.md).

El ejemplo siguiente genera C3638:

```
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
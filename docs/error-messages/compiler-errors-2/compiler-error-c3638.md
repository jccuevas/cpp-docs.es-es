---
title: Error del compilador C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 33bb248faf946c39543de4a14a44e2ebbda49880
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776754"
---
# <a name="compiler-error-c3638"></a>Error del compilador C3638

'operador': no se puede redefinir la conversión boxing estándar y los operadores de conversión unboxing

El compilador define un operador de conversión para cada clase administrada para admitir la conversión boxing implícita. Este operador no se puede redefinir.

Para obtener más información, consulte [conversión Boxing implícita](../../extensions/boxing-cpp-component-extensions.md).

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
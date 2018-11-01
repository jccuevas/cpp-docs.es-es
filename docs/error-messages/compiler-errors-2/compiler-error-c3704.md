---
title: Error del compilador C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 4e26742de6c294018f81c6f49c1719fdb11d5149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467124"
---
# <a name="compiler-error-c3704"></a>Error del compilador C3704

'function': un método vararg no puede desencadenar eventos

Se intentó utilizar [__event](../../cpp/event.md) en un método vararg. Para corregir este error, reemplace el `fireEvent(int i, ...)` llamar con la `fireEvent(int i)` llamar a como se muestra en el siguiente ejemplo de código.

El ejemplo siguiente genera C3704:

```
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```
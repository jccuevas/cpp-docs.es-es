---
title: Error del compilador C3704 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3704
dev_langs:
- C++
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4504534e3a53f37089f0b0ba045b7afde5a8065d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054992"
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
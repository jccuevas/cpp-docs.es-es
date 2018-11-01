---
title: Error del compilador C3748
ms.date: 11/04/2016
f1_keywords:
- C3748
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
ms.openlocfilehash: ef1c446f9feb3d40add62513a31fc81a382b98e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628415"
---
# <a name="compiler-error-c3748"></a>Error del compilador C3748

'interface': las interfaces administradas no pueden desencadenar eventos

El [__event](../../cpp/event.md) palabra clave no puede aparecer dentro de una interfaz.

El ejemplo siguiente genera C3748:

```
// C3748.cpp
__interface I {
// try the following line instead
// struct I {
   __event void f();   // C3748
};

int main() {
}
```
---
title: Error del compilador C2847
ms.date: 11/04/2016
f1_keywords:
- C2847
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
ms.openlocfilehash: 99c49be746cea6fb80c5e24667bcd97556a0ad04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481489"
---
# <a name="compiler-error-c2847"></a>Error del compilador C2847

no se puede aplicar sizeof al tipo administrado o WinRT 'class'

El [sizeof](../../cpp/sizeof-operator.md) operador obtiene el valor de un objeto en tiempo de compilación. El tamaño de un tipo de valor, una interfaz o una clase administrada o WinRT es dinámico y no puede conocerse en tiempo de compilación.

El ejemplo siguiente genera el error C2847:

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```

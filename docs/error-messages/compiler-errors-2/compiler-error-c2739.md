---
title: Error del compilador C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 18cece8d9630aa93e867329acc7cefea30da3286
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759664"
---
# <a name="compiler-error-c2739"></a>Error del compilador C2739

’number': las dimensiones de la matriz administrada o de WinRT explícita deben estar comprendidas entre 1 y 32

Una dimensión de matriz no estaba comprendida entre 1 y 32.

El ejemplo siguiente genera el error C2739 y muestra cómo corregirlo:

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```

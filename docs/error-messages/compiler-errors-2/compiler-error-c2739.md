---
title: Error del compilador C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: f7e7b20f64c8975e747fe84138cbcb18c3fd14fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258029"
---
# <a name="compiler-error-c2739"></a>Error del compilador C2739

’number': las dimensiones de la matriz administrada o de WinRT explícita deben estar comprendidas entre 1 y 32

Una dimensión de matriz no estaba comprendida entre 1 y 32.

El ejemplo siguiente genera el error C2739 y muestra cómo corregirlo:

```
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
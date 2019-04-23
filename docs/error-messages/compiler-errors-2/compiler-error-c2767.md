---
title: Error del compilador C2767
ms.date: 11/04/2016
f1_keywords:
- C2767
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
ms.openlocfilehash: 78b171b634aea66115c4029c696fec042593bb30
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777060"
---
# <a name="compiler-error-c2767"></a>Error del compilador C2767

administrado o falta de coincidencia de dimensión WinRTarray: se esperaban N argumentos - M proporcionado

Una declaración de matriz administrada o de WinRT estaba mal formada. Para obtener más información, vea [Matriz](../../extensions/arrays-cpp-component-extensions.md).

El siguiente ejemplo genera el error C2767 y muestra cómo corregirlo:

```
// C2767.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>(2,3); // C2767
   array<int> ^p2 = new array<int>(2);   // OK
}
```
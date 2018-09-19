---
title: Error del compilador C2767 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2767
dev_langs:
- C++
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6301471b4797bf3a1cb6f3936e54ab8bfb536b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051898"
---
# <a name="compiler-error-c2767"></a>Error del compilador C2767

administrado o falta de coincidencia de dimensión WinRTarray: se esperaban N argumentos - M proporcionado

Una declaración de matriz administrada o de WinRT estaba mal formada. Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).

El siguiente ejemplo genera el error C2767 y muestra cómo corregirlo:

```
// C2767.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>(2,3); // C2767
   array<int> ^p2 = new array<int>(2);   // OK
}
```
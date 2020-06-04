---
title: Error del compilador C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 332e0b253aed53f2adadf448b6a9c0681abc825e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747458"
---
# <a name="compiler-error-c3353"></a>Error del compilador C3353

'delegado': un delegado solo se puede crear desde una función global o una función miembro de un tipo WinRT o administrado

Los delegados, declarados con la palabra clave [Delegate](../../extensions/delegate-cpp-component-extensions.md) , solo se pueden declarar en el ámbito global.

El código siguiente genera el error C3353:

```cpp
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```

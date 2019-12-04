---
title: Error del compilador C2979
ms.date: 11/04/2016
f1_keywords:
- C2979
helpviewer_keywords:
- C2979
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
ms.openlocfilehash: 71953b360739765810fa047d65be9828d7d483da
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751563"
---
# <a name="compiler-error-c2979"></a>Error del compilador C2979

no se admite especializaciones explícitas en genéricos

Se declaró una clase genérica incorrectamente.  Para obtener más información, vea [genéricos](../../extensions/generics-cpp-component-extensions.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2979.

```cpp
// C2979.cpp
// compile with: /clr /c
generic <>
ref class Utils {};   // C2979 error

generic <class T>
ref class Utils2 {};   // OK
```

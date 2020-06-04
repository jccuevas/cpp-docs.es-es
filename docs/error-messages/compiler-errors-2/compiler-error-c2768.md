---
title: Error del compilador C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: bcc801bb5802598e936d577f08729214bb7e13a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759794"
---
# <a name="compiler-error-c2768"></a>Error del compilador C2768

' función ': uso no válido de argumentos de plantilla explícitos

El compilador no pudo determinar si una definición de función debía ser una especialización explícita de una plantilla de función o si se supone que la definición de función era para una nueva función.

Este error se presentó en Visual Studio .NET 2003, como parte de las mejoras de conformidad del compilador.

En el ejemplo siguiente se genera C2768:

```cpp
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```

---
title: Error del compilador C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: 9c0fb8fb0a98830aaf061ba980e7bdd7903f25e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257626"
---
# <a name="compiler-error-c2768"></a>Error del compilador C2768

'function': uso no válido de argumentos de plantilla explícitos

El compilador no pudo determinar si una definición de función se suponía que debía para ser una especialización explícita de una plantilla de función o si la definición de función se suponía que debía para ser para una nueva función.

Este error se introdujo en Visual Studio .NET 2003 como parte de las mejoras de conformidad del compilador.

El ejemplo siguiente genera C2768:

```
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
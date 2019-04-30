---
title: Advertencia del compilador (nivel 3) C4357
ms.date: 11/04/2016
f1_keywords:
- C4357
helpviewer_keywords:
- C4357
ms.assetid: 9259c633-3c02-4900-b94a-2d8d366d61cd
ms.openlocfilehash: a7923fdcda2a781c9680f8b3753fd101c73be19c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402026"
---
# <a name="compiler-warning-level-3-c4357"></a>Advertencia del compilador (nivel 3) C4357

param argumento de matriz en la lista de argumentos formal para el delegado 'del' omitir cuando se generen 'function'

El `ParamArray` omitió el atributo, y `function` no se puede llamar con argumentos variables.

El ejemplo siguiente genera C4357:

```
// C4357.cpp
// compile with: /clr /W3 /c
using namespace System;
public delegate void f(int i, ... array<Object^>^ varargs);   // C4357

public delegate void g(int i, array<Object^>^ varargs);   // OK
```
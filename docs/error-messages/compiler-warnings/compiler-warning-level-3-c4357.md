---
title: Advertencia del compilador (nivel 3) C4357
ms.date: 11/04/2016
f1_keywords:
- C4357
helpviewer_keywords:
- C4357
ms.assetid: 9259c633-3c02-4900-b94a-2d8d366d61cd
ms.openlocfilehash: 3af2e742bde40bc3787603e32efbc34e59dcb419
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198710"
---
# <a name="compiler-warning-level-3-c4357"></a>Advertencia del compilador (nivel 3) C4357

se omitió el argumento de matriz de parámetros en la lista de argumentos formales para el delegado ' del ' al generar ' función '

Se omitió el `ParamArray` atributo y no se puede llamar a `function` con argumentos variables.

En el ejemplo siguiente se genera C4357:

```cpp
// C4357.cpp
// compile with: /clr /W3 /c
using namespace System;
public delegate void f(int i, ... array<Object^>^ varargs);   // C4357

public delegate void g(int i, array<Object^>^ varargs);   // OK
```

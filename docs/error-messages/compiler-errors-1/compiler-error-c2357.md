---
title: Error del compilador C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: ce1926468bac7e44485be5c0a0944fdf12dce3d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759924"
---
# <a name="compiler-error-c2357"></a>Error del compilador C2357

' Identifier ': debe ser una función de tipo ' type '

El código declara una versión de la función `atexit` que no coincide con la versión declarada internamente por el compilador. Declare `atexit` como se indica a continuación:

```
int __cdecl atexit(void (__cdecl *)());
```

Para obtener más información, vea [init_seg](../../preprocessor/init-seg.md).

En el ejemplo siguiente se genera C2357:

```cpp
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```

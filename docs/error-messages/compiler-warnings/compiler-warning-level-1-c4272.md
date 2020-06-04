---
title: Advertencia del compilador (nivel 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 747b9e60ad2b8b0036c6eac50d44c2d70277384f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163110"
---
# <a name="compiler-warning-level-1-c4272"></a>Advertencia del compilador (nivel 1) C4272

' función ': está marcado como __declspec (dllimport); debe especificar la Convención de llamada nativa al importar una función.

Es un error exportar una función marcada con la Convención de llamada [__clrcall](../../cpp/clrcall.md) , y el compilador emite esta advertencia si intenta importar una función marcada como `__clrcall`.

En el ejemplo siguiente se genera C4272:

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```

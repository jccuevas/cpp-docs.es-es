---
title: Error del compilador C3395
ms.date: 11/04/2016
f1_keywords:
- C3395
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
ms.openlocfilehash: eaf63b42a6c44153a55d8aeb70f4f1174a5c895c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737548"
---
# <a name="compiler-error-c3395"></a>Error del compilador C3395

' función ': __declspec (dllexport) no se puede aplicar a una función con la \__clrcall Convención de llamada

`__declspec(dllexport)` y [__clrcall](../../cpp/clrcall.md) no son compatibles.  Para obtener más información, consulte [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

En el ejemplo siguiente se genera C3395:

```cpp
// C3395.cpp
// compile with: /clr /c

__declspec(dllexport) void __clrcall Test(){}   // C3395
void __clrcall Test2(){}   // OK
__declspec(dllexport) void Test3(){}   // OK
```

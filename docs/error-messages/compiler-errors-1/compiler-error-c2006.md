---
title: Error del compilador c2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 64f81929916cd3a4adf38a302ea34d46d9a5c070
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756557"
---
# <a name="compiler-error-c2006"></a>Error del compilador c2006

' Directive ' esperaba un nombre de archivo; se encontró ' token '

Las directivas como [#include](../../preprocessor/hash-include-directive-c-cpp.md) o [#import](../../preprocessor/hash-import-directive-cpp.md) requieren un nombre de archivo. Para resolver el error, asegúrese de que *token* sea un nombre de archivo válido. Además, ponga el nombre de archivo entre comillas dobles o corchetes angulares.

En el ejemplo siguiente se genera c2006:

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

Solución posible:

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```

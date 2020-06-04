---
title: Error del compilador C2710
ms.date: 11/04/2016
f1_keywords:
- C2710
helpviewer_keywords:
- C2710
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
ms.openlocfilehash: eea836f3508d750701b694421f660ce455d6f1f7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757454"
---
# <a name="compiler-error-c2710"></a>Error del compilador C2710

' Construct ': ' __declspec (modificador) ' solo se puede aplicar a una función que devuelve un puntero

Una función cuyo valor devuelto es un puntero es la única construcción a la que se puede aplicar `modifier`.

En el ejemplo siguiente se genera C2710:

```cpp
// C2710.cpp
__declspec(restrict) void f();   // C2710
// try the following line instead
__declspec(restrict) int * g();
```

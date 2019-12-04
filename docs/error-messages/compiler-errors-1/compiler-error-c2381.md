---
title: Error del compilador C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: 834b9939a99c694c702bb268b928575b4beb8856
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745400"
---
# <a name="compiler-error-c2381"></a>Error del compilador C2381

' función ': nueva definición; __declspec (noreturn) difiere

Una función se declaró y después se definió, pero la definición usaba el modificador de `__declspec` [Return](../../cpp/noreturn.md) . El uso de `noreturn` constituye una nueva definición de la función; la declaración y la definición deben estar de acuerdo en el uso de `noreturn`.

En el ejemplo siguiente se genera C2381:

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```

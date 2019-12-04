---
title: Error del compilador C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: a17bd95cf1727d058e0cbd9e3dfb93c500da9fb5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758260"
---
# <a name="compiler-error-c2637"></a>Error del compilador C2637

' Identifier ': no se pueden modificar los punteros a miembros de datos

Un puntero a un miembro de datos no puede tener una Convención de llamada. Para resolverlo, quite la Convención de llamada o declare un puntero a una función miembro.

En el ejemplo siguiente se genera C2637:

```cpp
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```

---
title: Error del compilador C2806
ms.date: 11/04/2016
f1_keywords:
- C2806
helpviewer_keywords:
- C2806
ms.assetid: 7c9ff1f4-1590-4c47-991d-b1075a173b48
ms.openlocfilehash: be991d26cb822221051316f3557b23a2b82e732d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760626"
---
# <a name="compiler-error-c2806"></a>Error del compilador C2806

' operator Operator ' tiene demasiados parámetros formales

Un operador sobrecargado tiene demasiados parámetros.

En el ejemplo siguiente se genera C2806:

```cpp
// C2806.cpp
// compile with: /c
class X {
public:
   X operator++ ( int, int );   // C2806 more than 1 parameter
   X operator++ ( int );   // OK
} ;
```

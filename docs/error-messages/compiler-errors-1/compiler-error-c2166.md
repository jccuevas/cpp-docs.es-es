---
title: Error del compilador C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: 36b4bcbd3eda213b840194cb635172a241f04b14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174724"
---
# <a name="compiler-error-c2166"></a>Error del compilador C2166

Valor L especifica un objeto const

El código intenta modificar un elemento declarado como `const`.

El ejemplo siguiente genera la advertencia C2166:

```
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```
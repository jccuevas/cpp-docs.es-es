---
title: Error del compilador C2787
ms.date: 11/04/2016
f1_keywords:
- C2787
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
ms.openlocfilehash: 00f2097dc556055f0becf1d81d784c9126c66f63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739602"
---
# <a name="compiler-error-c2787"></a>Error del compilador C2787

' Identifier ': no se ha asociado ningún GUID a este objeto

El operador [__uuidof](../../cpp/uuidof-operator.md) toma un tipo definido por el usuario con un GUID asociado o un objeto de este tipo definido por el usuario. Este error se produce cuando el argumento es un tipo definido por el usuario sin GUID.

En el ejemplo siguiente se genera C2787:

```cpp
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```

---
title: Error del compilador C2908
ms.date: 11/04/2016
f1_keywords:
- C2908
helpviewer_keywords:
- C2908
ms.assetid: 49cd2a21-cad8-4ba0-9a0b-3a0190d9344c
ms.openlocfilehash: ca07ef3c8240e6a55137e07bccbfc61ca8d96636
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750564"
---
# <a name="compiler-error-c2908"></a>Error del compilador C2908

especialización explícita; ya se ha creado una instancia de ' plantilla '

Una especialización de la plantilla principal se produce antes de la especialización explícita.

En el ejemplo siguiente se genera C2908:

```cpp
// C2908.cpp
// compile with: /c
template<class T> class X {};

void f() {
X<int> x;   //specialization and instantiation
            //of X<int>
}

template<> class X<int> {}  // C2908, explicit specialization
```

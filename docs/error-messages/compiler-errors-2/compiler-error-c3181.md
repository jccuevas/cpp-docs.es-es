---
title: Error del compilador C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: b37b28b4332b46aaaf803f58090a72c25e83f47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587764"
---
# <a name="compiler-error-c3181"></a>Error del compilador C3181

'type': operando no válido para el operador

Se pasó un parámetro no válido para el [typeid](../../windows/typeid-cpp-component-extensions.md) operador. El parámetro debe ser un tipo administrado.

Tenga en cuenta que el compilador utiliza alias para tipos nativos que se asignan a los tipos de common language runtime.

El ejemplo siguiente genera C3181:

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```

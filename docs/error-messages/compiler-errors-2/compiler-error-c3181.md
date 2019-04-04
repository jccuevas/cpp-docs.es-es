---
title: Error del compilador C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: dc848d4108ed4a1a7b6646647a1bbb1ec8dcadf7
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781814"
---
# <a name="compiler-error-c3181"></a>Error del compilador C3181

'type': operando no válido para el operador

Se pasó un parámetro no válido para el [typeid](../../extensions/typeid-cpp-component-extensions.md) operador. El parámetro debe ser un tipo administrado.

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

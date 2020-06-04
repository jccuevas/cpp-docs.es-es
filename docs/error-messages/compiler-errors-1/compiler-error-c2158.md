---
title: Error del compilador C2158
ms.date: 11/04/2016
f1_keywords:
- C2158
helpviewer_keywords:
- C2158
ms.assetid: 39028899-e95c-4809-8e65-6111118641ee
ms.openlocfilehash: f098af90d3052d6961eb0892085c02f2e42bbed4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755877"
---
# <a name="compiler-error-c2158"></a>Error del compilador C2158

'type': actualmente, la #pragma make_public solamente es compatible con tipos nativos que no sean de plantilla

La pragma [make_public](../../preprocessor/make-public.md) solo puede aplicarse a un tipo nativo que no sea de plantilla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2158.

```cpp
// C2158.cpp
// compile with: /clr /c
ref class A {};
#pragma make_public(A)   // C2158

template< typename T >
class B {};
#pragma make_public(B)   // C2158
#pragma make_public(B<int>)   // C2158

void C () {}
#pragma make_public(C)   // C2158

class D {};
#pragma make_public(D)   // OK
```

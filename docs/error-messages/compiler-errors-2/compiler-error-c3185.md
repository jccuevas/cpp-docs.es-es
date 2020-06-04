---
title: Error del compilador error c3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 36f350287a1cfaf937ee739800042aaf99f31769
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761639"
---
# <a name="compiler-error-c3185"></a>Error del compilador error c3185

'typeid' usado en un tipo ’type’ administrado o de WinRT; use 'operator' en su lugar

No se puede aplicar el operador [typeid](../../cpp/typeid-operator.md) a un tipo administrado o WinRT; Utilice [typeid](../../extensions/typeid-cpp-component-extensions.md) en su lugar.

El ejemplo siguiente genera el error C3185 y muestra cómo corregirlo:

```cpp
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```

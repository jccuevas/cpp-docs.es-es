---
title: Error del compilador C3830
ms.date: 11/04/2016
f1_keywords:
- C3830
helpviewer_keywords:
- C3830
ms.assetid: c9798f88-5001-4067-9fb1-09957ddc6fa8
ms.openlocfilehash: 14272d2c0b0f8de63f55d2ba3d1c01cf04e0dfbd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741643"
---
# <a name="compiler-error-c3830"></a>Error del compilador C3830

' tipo1 ': no se puede heredar de ' tipo2 ', los tipos de valor solo pueden heredar de clases de interfaz

Un tipo de valor no puede heredar una clase base.  Para más información, vea [ref class and ref struct (C++/CLI and C++/CX)](../../extensions/classes-and-structs-cpp-component-extensions.md) [ref class y ref struct (C++/CLI y C++/CX)].

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3830:

```cpp
// C3830a.cpp
// compile with: /clr /c
public value struct MyStruct4 {
   int i;
};

public value class MyClass : public MyStruct4 {};   // C3830

// OK
public interface struct MyInterface4 {
   void i();
};

public value class MyClass2 : public MyInterface4 {
public:
   virtual void i(){}
};
```

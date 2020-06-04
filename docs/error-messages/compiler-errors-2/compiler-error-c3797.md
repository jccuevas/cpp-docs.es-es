---
title: Error del compilador C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 7236cb75aef4250440a1e992415df07fb5b7da3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757181"
---
# <a name="compiler-error-c3797"></a>Error del compilador C3797

' override ': la declaración de evento no puede tener un especificador de invalidación (en su lugar, debe colocarse en métodos Add/Remove/raise)

No se puede invalidar un evento trivial (un evento sin métodos de descriptor de acceso definidos explícitamente) con otro evento trivial. El evento de reemplazo debe definir su comportamiento con las funciones de descriptor de acceso.

Para obtener más información, vea [Event](../../extensions/event-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3797.

```cpp
// C3797.cpp
// compile with: /clr /c
delegate void MyDel();

ref class Class1 {
public:
   virtual event MyDel ^ E;
};

ref class Class2 : public Class1 {
public:
   virtual event MyDel ^ E override;   // C3797
};

// OK
ref class Class3 : public Class1 {
public:
   virtual event MyDel ^ E {
      void add(MyDel ^ d) override {}
      void remove(MyDel ^ d) override {}
   }
};
```

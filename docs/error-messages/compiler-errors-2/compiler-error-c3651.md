---
title: Error del compilador C3651
ms.date: 11/04/2016
f1_keywords:
- C3651
helpviewer_keywords:
- C3651
ms.assetid: a03e692e-c219-4654-9827-8415cfa5a22d
ms.openlocfilehash: 6e773201e3bc9a4edb1ee77f1ddcd555e0ae0c0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388688"
---
# <a name="compiler-error-c3651"></a>Error del compilador C3651

'member': no se puede utilizar como invalidación explícita, debe ser miembro de una clase base

Se especificó un reemplazo explícito, pero la función que se está reemplaza estaba en un tipo que no es un tipo base.

Para obtener más información, consulte [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).

El ejemplo siguiente genera C3651:

```
// C3651.cpp
// compile with: /clr /c
ref class C {
public:
   virtual void func2();
};

ref class Other {
public:
   virtual void func();
};

ref class D : public C {
public:
   virtual void func() new sealed = Other::func;   // C3651
   virtual void func2() new sealed = C::func2;   // OK
};
```
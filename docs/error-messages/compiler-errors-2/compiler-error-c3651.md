---
title: Error del compilador C3651
ms.date: 11/04/2016
f1_keywords:
- C3651
helpviewer_keywords:
- C3651
ms.assetid: a03e692e-c219-4654-9827-8415cfa5a22d
ms.openlocfilehash: 5601dd2f510e4322e67f49478eefce795312e380
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494187"
---
# <a name="compiler-error-c3651"></a>Error del compilador C3651

'member': no se puede utilizar como invalidación explícita, debe ser miembro de una clase base

Se especificó un reemplazo explícito, pero la función que se está reemplaza estaba en un tipo que no es un tipo base.

Para obtener más información, consulte [invalidaciones explícitas](../../windows/explicit-overrides-cpp-component-extensions.md).

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
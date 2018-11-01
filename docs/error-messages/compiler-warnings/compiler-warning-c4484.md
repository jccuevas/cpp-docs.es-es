---
title: Advertencia del compilador C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 71a3d903ba32fecac4b2d8bfc3e0a93f19d0f4ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473182"
---
# <a name="compiler-warning-c4484"></a>Advertencia del compilador C4484

'función_de_reemplazo': coincide con el método de clase ref base 'función_de_clase_base', pero no está marcado como 'virtual', 'new' u 'override'; se supone 'new' (y no 'virtual')

Cuando se compila con **/CLR**, el compilador no invalidará implícitamente una función de la clase base, lo que significa que la función obtendrá una nueva ranura en vtable. Para resolver, especifique explícitamente si una función es una invalidación.

Para obtener más información, consulte:

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../windows/override-cpp-component-extensions.md)

- [New (nueva ranura en vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 siempre se emite como un error. Use la [advertencia](../../preprocessor/warning.md) pragma para suprimir C4484.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4484.

```
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```
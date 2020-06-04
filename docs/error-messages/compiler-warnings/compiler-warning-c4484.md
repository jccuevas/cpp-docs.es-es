---
title: Advertencia del compilador C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: c168c91f8259b744ed10dd72701d34fd60b98681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165163"
---
# <a name="compiler-warning-c4484"></a>Advertencia del compilador C4484

' override_function ': coincide con el método de clase Ref base ' base_class_function ', pero no está marcado como ' virtual ', ' New ' u ' override '; se presupone ' New ' (y no ' virtual ')

Cuando se compila con **/CLR**, el compilador no reemplazará implícitamente una función de clase base, lo que significa que la función obtendrá una nueva ranura en la tabla vtable. Para resolverlo, especifique explícitamente si una función es una invalidación.

Para más información, consulte:

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [new (nueva ranura en vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 siempre se emite como un error. Use la pragma [Warning](../../preprocessor/warning.md) para suprimir C4484.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4484.

```cpp
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

---
title: Advertencia del compilador C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: c92f805eb2960336ed34f5da93b6c13f46bf15ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165150"
---
# <a name="compiler-warning-c4485"></a>Advertencia del compilador C4485

' override_function ': coincide con el método de clase Ref base ' base_class_function ', pero no está marcado como ' New ' u ' override '; se presupone ' New ' (y ' virtual ')

Un descriptor de acceso invalida, con o sin la palabra clave `virtual`, una función de descriptor de acceso de clase base, pero el especificador `override` o `new` no formaba parte de la firma de la función de reemplazo. Agregue el especificador `new` o `override` para resolver esta advertencia.

Vea [override](../../extensions/override-cpp-component-extensions.md) y [New (New slot in vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) para obtener más información.

C4485 siempre se emite como un error. Use la pragma [Warning](../../preprocessor/warning.md) para suprimir C4485.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4485

```cpp
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```

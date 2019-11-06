---
title: ADVERTENCIA del compilador C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 896fca6c6b257c90ccdf813a9c6cb6bc27ad9e96
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623620"
---
# <a name="compiler-warning-c4485"></a>ADVERTENCIA del compilador C4485

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
---
title: Advertencia del compilador C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: a2298f5369ff941a9d5ac38838f531d6db478739
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165098"
---
# <a name="compiler-warning-c4867"></a>Advertencia del compilador C4867

' función ': falta la lista de argumentos de la llamada de función; usar ' Call ' para crear un puntero a un miembro

Un puntero a una función miembro se inicializó incorrectamente.

Esta advertencia se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: cumplimiento de puntero a miembro mejorado.  El código que se compiló antes de Visual Studio 2005 generará ahora C4867.

Esta advertencia siempre se emite como error. Para deshabilitar esta advertencia, use la pragma [warning](../../preprocessor/warning.md) . Para obtener más información sobre C4867 y MFC/ATL, vea [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4867.

```cpp
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```

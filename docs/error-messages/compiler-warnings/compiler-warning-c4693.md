---
title: Advertencia del compilador C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: cac5918eb4a1689fd215e07272958eeca48247ad
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781905"
---
# <a name="compiler-warning-c4693"></a>Advertencia del compilador C4693

> 'class': una clase abstracta sealed no puede tener miembros de instancia 'Test'

Si un tipo se marca [sealed](../../extensions/sealed-cpp-component-extensions.md) y [abstracta](../../extensions/abstract-cpp-component-extensions.md), sólo puede tener miembros estáticos.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [advertencia #pragma](../../preprocessor/warning.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4693.

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```
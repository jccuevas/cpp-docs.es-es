---
title: Advertencia del compilador C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 49d101ea56cd868e18489b6c74724a2d106c9265
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536664"
---
# <a name="compiler-warning-c4693"></a>Advertencia del compilador C4693

> 'class': una clase abstracta sealed no puede tener miembros de instancia 'Test'

Si un tipo se marca [sealed](../../windows/sealed-cpp-component-extensions.md) y [abstracta](../../windows/abstract-cpp-component-extensions.md), sólo puede tener miembros estáticos.

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
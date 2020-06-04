---
title: Advertencia del compilador C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 71c3db18b400ce94bff3c643d6728a6613061039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165137"
---
# <a name="compiler-warning-c4693"></a>Advertencia del compilador C4693

> 'class': una clase abstracta sealed no puede tener miembros de instancia 'Test'

Si un tipo se marca como [sellado](../../extensions/sealed-cpp-component-extensions.md) y [abstracto](../../extensions/abstract-cpp-component-extensions.md), solo puede tener miembros estáticos.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [#pragma ADVERTENCIA](../../preprocessor/warning.md).

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

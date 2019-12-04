---
title: Error del compilador C3657
ms.date: 11/04/2016
f1_keywords:
- C3657
helpviewer_keywords:
- C3657
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
ms.openlocfilehash: b1a72fc3d96a5ef3a591fb61d0b2839fb5c1b05b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758274"
---
# <a name="compiler-error-c3657"></a>Error del compilador C3657

los destructores no se pueden invalidar explícitamente ni se pueden invalidar explícitamente

Los destructores o finalizadores no se pueden invalidar explícitamente. Para obtener más información, vea [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3657.

```cpp
// C3657.cpp
// compile with: /clr
public ref struct I {
   virtual ~I() { }
   virtual void a();
};

public ref struct D : I {
   virtual ~D() = I::~I {}   // C3657
   virtual void a() = I::a {}   // OK
};
```

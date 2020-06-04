---
title: Error del compilador C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 2b57f3346427ff548d11fe776e909eca99433a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749040"
---
# <a name="compiler-error-c3908"></a>Error del compilador C3908

nivel de acceso menos restrictivo que ' construcción '

Un método de descriptor de acceso de propiedad (get o set) no puede tener un acceso menos restrictivo que el acceso especificado en la propia propiedad.  De forma similar, para los métodos de descriptor de acceso de eventos

Para obtener más información, vea [propiedad](../../extensions/property-cpp-component-extensions.md) y [evento](../../extensions/event-cpp-component-extensions.md).

En el ejemplo siguiente se genera C3908:

```cpp
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```

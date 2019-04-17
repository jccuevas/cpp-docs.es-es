---
title: Error del compilador C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: e11d830c3d662ea424caadeb50df669700f8c78f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58766760"
---
# <a name="compiler-error-c3908"></a>Error del compilador C3908

nivel de acceso menos restrictivo que 'construct'

Un método de descriptor de acceso de propiedad (get o set) no puede tener acceso menos restrictivo que el acceso especificado en la propiedad propiamente dicha.  De forma similar, para los métodos de descriptor de acceso de eventos.

Para obtener más información, consulte [propiedad](../../extensions/property-cpp-component-extensions.md) y [eventos](../../extensions/event-cpp-component-extensions.md).

El ejemplo siguiente genera C3908:

```
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
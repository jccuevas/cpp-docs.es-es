---
title: Error del compilador C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 84b21f20cbc8203a9cd70e487738c34c6ad3a89b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598938"
---
# <a name="compiler-error-c3908"></a>Error del compilador C3908

nivel de acceso menos restrictivo que 'construct'

Un método de descriptor de acceso de propiedad (get o set) no puede tener acceso menos restrictivo que el acceso especificado en la propiedad propiamente dicha.  De forma similar, para los métodos de descriptor de acceso de eventos.

Para obtener más información, consulte [propiedad](../../windows/property-cpp-component-extensions.md) y [eventos](../../windows/event-cpp-component-extensions.md).

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
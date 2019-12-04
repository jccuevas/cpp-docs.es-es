---
title: Error del compilador C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: f1289fb9a4d60f2c75b54fd573c83064f1517282
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749105"
---
# <a name="compiler-error-c3900"></a>Error del compilador C3900

' Member ': no se permite en el ámbito actual

Los bloques de propiedades solo pueden contener declaraciones de función y definiciones de funciones insertadas. No se permiten miembros que no sean funciones en los bloques de propiedades. No se permite ninguna TypeDef, operador o función Friend. Para obtener más información, consulta [property](../../extensions/property-cpp-component-extensions.md).

Las definiciones de eventos solo pueden contener métodos y funciones de acceso.

En el ejemplo siguiente se genera C3900:

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

En el ejemplo siguiente se genera C3900:

```cpp
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```

---
title: Error del compilador C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: d031b55407d108b4f8be362156911bfae688326a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512364"
---
# <a name="compiler-error-c3900"></a>Error del compilador C3900

'member': no se permite en el ámbito actual

Bloques de propiedad pueden contener declaraciones de función y definiciones de funciones insertadas solo. Ningún miembro que no sean funciones se permite en los bloques de propiedades. No se permiten funciones de definiciones de tipos, operadores o friend. Para obtener más información, consulta [property](../../windows/property-cpp-component-extensions.md).

Las definiciones de eventos sólo pueden contener funciones y métodos de acceso.

El ejemplo siguiente genera C3900:

```
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

El ejemplo siguiente genera C3900:

```
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
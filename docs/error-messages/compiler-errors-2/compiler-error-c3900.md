---
title: Error del compilador C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 35df94ccfcd7942f9057cb37ceee349c09b80607
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776254"
---
# <a name="compiler-error-c3900"></a>Error del compilador C3900

'member': no se permite en el ámbito actual

Bloques de propiedad pueden contener declaraciones de función y definiciones de funciones insertadas solo. Ningún miembro que no sean funciones se permite en los bloques de propiedades. No se permiten funciones de definiciones de tipos, operadores o friend. Para obtener más información, consulta [property](../../extensions/property-cpp-component-extensions.md).

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
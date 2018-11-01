---
title: Error del compilador C3901
ms.date: 11/04/2016
f1_keywords:
- C3901
helpviewer_keywords:
- C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
ms.openlocfilehash: 0c5b561f0e650ace69e09d33942f2036b9ee91ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677271"
---
# <a name="compiler-error-c3901"></a>Error del compilador C3901

'función_de_descriptores_de_acceso': debe tener el tipo de valor devuelto 'type'

Tipo de valor devuelto del método get de al menos uno debe coincidir con el tipo de propiedad. Para obtener más información, consulta [property](../../windows/property-cpp-component-extensions.md).

El ejemplo siguiente genera C3901:

```
// C3901.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String^ Name {
      void get();   // C3901
      // try the following line instead
      // String^ get();
   };
};

ref class Y {
   property double values[int, int] {
      int get(int, int);   // C3901
      // try the following line instead
      // double get(int, int);
   };
};
```
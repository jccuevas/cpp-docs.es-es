---
title: Error del compilador C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 0fe7e61c28ad2688a6d97b4164c2b5cfa81a37b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474872"
---
# <a name="compiler-error-c3919"></a>Error del compilador C3919

'método del evento': función debe tener el tipo 'type'

No se declaró correctamente un método de descriptor de acceso de eventos.

Para obtener más información acerca de los eventos, vea [eventos](../../windows/event-cpp-component-extensions.md).

El ejemplo siguiente genera C3919:

```
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```
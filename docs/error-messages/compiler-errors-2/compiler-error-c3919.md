---
title: Error del compilador C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 05ac2fc9258a078f352b6012e64e86fe4b70c3f0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771479"
---
# <a name="compiler-error-c3919"></a>Error del compilador C3919

'método del evento': función debe tener el tipo 'type'

No se declaró correctamente un método de descriptor de acceso de eventos.

Para obtener más información acerca de los eventos, vea [eventos](../../extensions/event-cpp-component-extensions.md).

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
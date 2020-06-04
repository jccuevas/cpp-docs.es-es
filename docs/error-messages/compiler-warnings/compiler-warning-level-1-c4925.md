---
title: Advertencia del compilador (nivel 1) C4925
ms.date: 11/04/2016
f1_keywords:
- C4925
helpviewer_keywords:
- C4925
ms.assetid: a4b206c0-016a-4f28-873a-bb8bb41bad50
ms.openlocfilehash: defd60d02a8725b114b3901f8d70af87e27445c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174640"
---
# <a name="compiler-warning-level-1-c4925"></a>Advertencia del compilador (nivel 1) C4925

'method': no se puede llamar al método dispinterface desde el script

Lenguajes de scripting no pueden crear un parámetro VT_BYREF 'in', solo puede crear parámetros VT_BYREF 'out'.

Otra manera de resolver esta advertencia es no convertir el parámetro (en la definición e implementación) en un tipo de puntero.

El ejemplo siguiente genera la advertencia C4925:

```cpp
// C4925.cpp
// compile with: /LD /W1
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[ module(name="Test")];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IDisp {
   [id(9)] void f([in] int*);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002")  ]
struct CDisp : IDisp {   // C4925
   void f(int*) {}
};
```

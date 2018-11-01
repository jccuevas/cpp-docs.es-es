---
title: Advertencia del compilador (nivel 1) C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: 07081f2b8e305e20eb1725d3d76a6d77638caa7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651716"
---
# <a name="compiler-warning-level-1-c4929"></a>Advertencia del compilador (nivel 1) C4929

'archivo': biblioteca de tipos contiene una unión; se omitirá el calificador 'embedded_idl'

El atributo embedded_idl de [#import](../../preprocessor/hash-import-directive-cpp.md) no se pueden aplicar a la biblioteca de tipos porque una unión está presente en la biblioteca de tipos. Para resolver esta advertencia, no utilice embedded_idl.

## <a name="example"></a>Ejemplo

El ejemplo siguiente define un componente.

```
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4929.

```
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```
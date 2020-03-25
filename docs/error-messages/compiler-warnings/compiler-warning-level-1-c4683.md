---
title: Advertencia del compilador (nivel 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: f86cf8f6d894d6efaa1b49977634956dc1979a98
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175434"
---
# <a name="compiler-warning-level-1-c4683"></a>Advertencia del compilador (nivel 1) C4683

> '*función*': el origen del evento tiene un parámetro ' out' '; Tenga cuidado al enlazar varios controladores de eventos

## <a name="remarks"></a>Observaciones

Si hay más de un receptor de eventos escuchando a un origen de eventos COM, el valor de un parámetro de salida se puede omitir.

Tenga en cuenta que se producirá una fuga de memoria en las situaciones siguientes:

1. Si un método tiene un parámetro de salida que se asigna internamente, por ejemplo, un BSTR *.

2. Si el evento tiene más de un controlador (es un evento de multidifusión).

La razón de la fuga es que el parámetro out se establecerá en más de un controlador, pero solo lo devolverá el último controlador al sitio de llamada.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4683 y se muestra cómo corregirlo:

```cpp
// C4683.cpp
// compile with: /W1 /LD
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="xx") ];

[ object ]
__interface I {
   HRESULT f([out] int* pi);
   // try the following line instead
   // HRESULT f(int* pi);
};

[ coclass, event_source(com) ]
struct E {
   __event __interface I;   // C4683
};
```

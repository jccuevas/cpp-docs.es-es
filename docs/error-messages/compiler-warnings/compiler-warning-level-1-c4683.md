---
title: Compilador advertencia (nivel 1) C4683 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a157d3beb7c2efa7f1144a961973652e2ce384f7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194202"
---
# <a name="compiler-warning-level-1-c4683"></a>Advertencia del compilador (nivel 1) C4683

> '*función*': origen de eventos tiene un 'out'-parámetro; tenga cuidado al enlazar varios controladores de eventos

## <a name="remarks"></a>Comentarios

Si más de un receptor de eventos está escuchando en un origen de eventos COM, se puede omitir el valor de un parámetro de salida.

Tenga en cuenta que se producirá una pérdida de memoria en las situaciones siguientes:

1. Si un método tiene un parámetro de salida asignado internamente, por ejemplo un BSTR *.

2. Si el evento tiene más de un controlador (es un evento de multidifusión).

El motivo de la pérdida es que el parámetro de salida se establece más de un controlador, pero al sitio de llamada sólo devuelve el último controlador.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4683 y muestra cómo corregirlo:

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
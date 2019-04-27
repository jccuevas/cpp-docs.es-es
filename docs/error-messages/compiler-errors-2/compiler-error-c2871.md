---
title: Error del compilador C2871
ms.date: 11/04/2016
f1_keywords:
- C2871
helpviewer_keywords:
- C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
ms.openlocfilehash: 355a485de46916977be6f7b801794806a9c9e0ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165197"
---
# <a name="compiler-error-c2871"></a>Error del compilador C2871

'name': no existe un espacio de nombres con este nombre

Este error se producirá cuando se pasa un identificador que no sea un espacio de nombres para un [mediante](../../cpp/namespaces-cpp.md#using_directives) directiva.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2871:

```cpp
// C2871.cpp
// compile with: /c
namespace a {
   int fn(int i) { return i; }
}
namespace b {
   using namespace d;   // C2871 because d is not a namespace
   using namespace a;   // OK
}
```
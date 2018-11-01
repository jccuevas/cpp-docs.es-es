---
title: Advertencia del compilador (nivel 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5ec0aea543053d699db7483df7dd7ea91b3af715
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594550"
---
# <a name="compiler-warning-level-1-c4716"></a>Advertencia del compilador (nivel 1) C4716

'function': la función debe devolver un valor

La función especificada no devolvió un valor.

Solo funciona con un tipo de valor devuelto void pueden usa el comando devuelto sin un valor devuelto correspondiente.

Cuando se llama a esta función, se devolverá un valor indefinido.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [advertencia #pragma](../../preprocessor/warning.md).

El ejemplo siguiente genera C4716:

```
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```
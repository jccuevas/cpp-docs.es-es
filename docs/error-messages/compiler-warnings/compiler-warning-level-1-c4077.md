---
title: Advertencia del compilador (nivel 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: fb9684b812e039bd37278f9f27db9225d0131f23
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626906"
---
# <a name="compiler-warning-level-1-c4077"></a>Advertencia del compilador (nivel 1) C4077

opción check_stack desconocida

El formato antiguo de la pragma **check_stack** se usa con un argumento desconocido. El argumento debe ser `+`, `-`, `(on)`, `(off)`o estar vacío.

El compilador omite la pragma y deja la comprobación de la pila sin cambios.

## <a name="example"></a>Ejemplo

```cpp
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```
---
title: ADVERTENCIA del compilador (nivel 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: d36031aa9a831d4669d796d8a40292e2d6ba15a8
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964974"
---
# <a name="compiler-warning-level-1-c4606"></a>ADVERTENCIA del compilador (nivel 1) C4606

\#pragma warning: ' warning_number ' omitido; Las advertencias de análisis de código no están asociadas a los niveles de advertencia

En el caso de las advertencias de análisis de código, solo se admiten `error`, `once`y `default` con la pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4606.

```cpp
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```
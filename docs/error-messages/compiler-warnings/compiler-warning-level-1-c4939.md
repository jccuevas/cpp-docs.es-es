---
title: Advertencia del compilador (nivel 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 5c87dad744281464599ee6c28b5bcf6e350b9feb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199282"
---
# <a name="compiler-warning-level-1-c4939"></a>Advertencia del compilador (nivel 1) C4939

\#pragma vtordisp está en desuso y se quitará en una versión futura de VisualC++

Se quitará la pragma [vtordisp](../../preprocessor/vtordisp.md) en próximas versiones de Visual C++

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4939:

```cpp
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```

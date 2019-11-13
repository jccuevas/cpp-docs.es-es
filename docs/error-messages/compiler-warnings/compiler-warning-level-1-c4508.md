---
title: ADVERTENCIA del compilador (nivel 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 394a59a472100cc30476b5bb87f30c45d867f94b
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966305"
---
# <a name="compiler-warning-level-1-c4508"></a>ADVERTENCIA del compilador (nivel 1) C4508

' función ': la función debe devolver un valor; se supone el tipo de valor devuelto ' void '

La función no tiene ningún tipo de valor devuelto especificado. En este caso, también se debe activar C4430 y el compilador implementa la corrección indicada por C4430 (el valor predeterminado es int).

Para resolver esta advertencia, declare explícitamente el tipo de valor devuelto de las funciones.

En el ejemplo siguiente se genera C4508:

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```
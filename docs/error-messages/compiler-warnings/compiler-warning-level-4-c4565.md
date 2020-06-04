---
title: Advertencia del compilador (nivel 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: 5eccb3c29da612a39f7fcdf4ef25dedb898c8d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198333"
---
# <a name="compiler-warning-level-4-c4565"></a>Advertencia del compilador (nivel 4) C4565

> '*función*': nueva definición; el símbolo se declaró previamente con __declspec (*modificador*)

## <a name="remarks"></a>Observaciones

Se redefinió o volvió a declarar un símbolo y la segunda definición o declaración, a diferencia de la primera definición o declaración, no tenía un modificador `__declspec` (*modificador*). Esta advertencia es informativa. Para corregir esta advertencia, elimine una de las definiciones.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```

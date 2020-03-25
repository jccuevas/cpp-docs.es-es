---
title: Advertencia del compilador (nivel 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 0788824dd4180476d81d9682f99fb95883b8c4f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198346"
---
# <a name="compiler-warning-level-4-c4559"></a>Advertencia del compilador (nivel 4) C4559

> '*función*': nueva definición; la función obtiene __declspec (*modificador*)

## <a name="remarks"></a>Observaciones

Se redefinió o se volvió a declarar una función y la segunda definición o declaración agregó un modificador **__declspec** (*modificador*). Esta advertencia es informativa. Para corregir esta advertencia, elimine una de las definiciones.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```

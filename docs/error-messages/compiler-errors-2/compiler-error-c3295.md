---
title: Error del compilador C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 4ee79e87085b0b939a762fec4c576c393846c2ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756869"
---
# <a name="compiler-error-c3295"></a>Error del compilador C3295

'#pragma pragma' solo se puede usar en un ámbito global o de espacio de nombres

Algunas pragmas no se pueden usar en una función.  Vea [directivas pragma y la palabra clave __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3295.

```cpp
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```

---
title: Error del compilador C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: 504b13aeb37fae0c350ef88798fefaec6f26c8e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757831"
---
# <a name="compiler-error-c3645"></a>Error del compilador C3645

' función ': no se puede usar __clrcall en funciones compiladas en código nativo

La presencia de algunas palabras clave en una función hará que la función se compile en modo nativo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3645.

```cpp
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```

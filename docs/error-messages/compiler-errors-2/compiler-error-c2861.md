---
title: Error del compilador C2861
ms.date: 11/04/2016
f1_keywords:
- C2861
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
ms.openlocfilehash: 3d6cab186d4acf229a32620f33c9c86e807459dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751994"
---
# <a name="compiler-error-c2861"></a>Error del compilador C2861

' nombre de función ': no se puede definir una función miembro de interfaz

El compilador encontró la palabra clave interface o dedujo un struct como una interfaz pero, a continuación, encontró una definición de función miembro.  Una interfaz no puede contener una definición para una función miembro.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2861:

```cpp
// C2861.cpp
// compile with: /c
#include <objbase.h>   // required for IUnknown definition
[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IMyInterface : IUnknown {
   HRESULT mf(int a);
};

HRESULT IMyInterface::mf(int a) {}   // C2861
```

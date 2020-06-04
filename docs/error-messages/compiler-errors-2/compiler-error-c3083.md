---
title: Error del compilador C3083
ms.date: 11/04/2016
f1_keywords:
- C3083
helpviewer_keywords:
- C3083
ms.assetid: 05ff791d-52bb-41eb-9511-3ef89d7f4710
ms.openlocfilehash: ee4a2bc683a757e079295c16d1022739eaa5726c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759716"
---
# <a name="compiler-error-c3083"></a>Error del compilador C3083

' función ': el símbolo a la izquierda de ':: ' debe ser un tipo

Se llamó a una función de forma incorrecta.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3083.

```cpp
// C3083.cpp
// compile with: /c
struct N {
   ~N();
};

struct N1 {
   ~N1();
};

N::N::~N() {}   // C3083
N1::~N1() {}   // OK
```

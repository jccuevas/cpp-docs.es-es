---
title: Error del compilador C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 85cac4919c048c30a3ed1ff5573a3c14b77da0bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737197"
---
# <a name="compiler-error-c2178"></a>Error del compilador C2178

'*Identifier*' no se puede declarar con el especificador '*Specifier*'

Se usó un especificador de `mutable` en una declaración, pero el especificador no se permite en este contexto.

El especificador de `mutable` solo se puede aplicar a los nombres de los miembros de datos de clase y no se puede aplicar a los nombres declarados `const` o `static`, y no se pueden aplicar a los miembros de referencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo puede producirse C2178 y cómo corregirlo.

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```

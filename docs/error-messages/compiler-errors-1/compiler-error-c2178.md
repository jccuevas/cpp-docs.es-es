---
title: Error de compilador C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: cd153bb5b331872bfe35b046d41612998bd0eff7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386010"
---
# <a name="compiler-error-c2178"></a>Error de compilador C2178

'*identificador*'no se pueden declarar con'*especificador*' especificador

Un `mutable` especificador se usó en una declaración, pero el especificador no se permite en este contexto.

El `mutable` especificador pueden aplicarse únicamente a los nombres de miembros de datos de clase y no se puede aplicar a los nombres declarados `const` o `static`y no se puede aplicar para hacer referencia a miembros.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo puede producirse C2178 y cómo corregirlo.

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```

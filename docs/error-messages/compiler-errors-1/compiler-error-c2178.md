---
title: Error de compilador C2178 | Microsoft Docs
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9efdb3258e6793a17a26b552df8ba4e63c9107
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102344"
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

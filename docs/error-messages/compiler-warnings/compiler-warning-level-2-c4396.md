---
title: Del compilador (nivel 2) de la advertencia C4396 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa0a084e90db9d48f517bfe65c6340eb532f0ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118575"
---
# <a name="compiler-warning-level-2-c4396"></a>Advertencia del compilador (nivel 2) C4396

"name": el especificador inline no se puede usar cuando una declaración de confianza hace referencia a una especialización de una plantilla de función

Una especialización de una plantilla de función no puede especificar cualquiera de los [inline](../../cpp/inline-functions-cpp.md) especificadores. El compilador emite la advertencia C4396 y omite el especificador inline.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite el especificador `inline`, `__inline`o `__forceinline` de la declaración de función friend.

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente muestra una declaración de función friend no válida con un especificador `inline` .

```
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```
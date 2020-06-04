---
title: Advertencia del compilador (nivel 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: f37fcc7ece09bb9028a522ec6baf85d0e0e585c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161820"
---
# <a name="compiler-warning-level-2-c4396"></a>Advertencia del compilador (nivel 2) C4396

"name": el especificador inline no se puede usar cuando una declaración de confianza hace referencia a una especialización de una plantilla de función

Una especialización de una plantilla de función no puede especificar ninguno de los especificadores [inline](../../cpp/inline-functions-cpp.md) . El compilador emite la advertencia C4396 y omite el especificador inline.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite el especificador `inline`, `__inline`o `__forceinline` de la declaración de función friend.

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente muestra una declaración de función friend no válida con un especificador `inline` .

```cpp
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

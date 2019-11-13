---
title: Advertencia del compilador (nivel 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: e874e00d44eef29240cca55541837facfcf64495
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052040"
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
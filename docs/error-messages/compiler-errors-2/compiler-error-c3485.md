---
title: Error del compilador C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 0eacb6ce6426674d23fc78596ead3730f46ae370
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743047"
---
# <a name="compiler-error-c3485"></a>Error del compilador C3485

una definición de lambda no puede tener ningún calificador cv

No puede usar un calificador `const` o `volatile` como parte de la definición de una expresión lambda.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite el calificador `const` o `volatile` de la definición de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3485 porque usa el calificador `const` como parte de la definición de una expresión lambda:

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)

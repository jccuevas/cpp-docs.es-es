---
title: Error del compilador C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: c9895a3e5a8ae7e941fccde2da85fedfb3d2c6dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743125"
---
# <a name="compiler-error-c3484"></a>Error del compilador C3484

se esperaba '->' antes del tipo de valor devuelto

Se debe proporcionar `->` antes del tipo de valor devuelto de una expresión lambda.

### <a name="to-correct-this-error"></a>Para corregir este error

- Proporcione `->` antes del tipo de valor devuelto.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3484:

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se resuelve el error C3484 al proporcionar `->` antes del tipo de valor devuelto de la expresión lambda:

```cpp
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)

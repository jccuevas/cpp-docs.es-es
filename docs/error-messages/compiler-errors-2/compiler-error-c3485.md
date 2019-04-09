---
title: Error del compilador C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2fcaecd6be35e2ae6822133930b48b6bbf02aafe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027589"
---
# <a name="compiler-error-c3485"></a>Error del compilador C3485

una definición de lambda no puede tener ningún calificador cv

No puede usar un calificador `const` o `volatile` como parte de la definición de una expresión lambda.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite el calificador `const` o `volatile` de la definición de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3485 porque usa el calificador `const` como parte de la definición de una expresión lambda:

```
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
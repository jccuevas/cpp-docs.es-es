---
title: Error del compilador C3485 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3485
dev_langs:
- C++
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3eee53f23aa2cdc958b63faed11ead302f4b1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060751"
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
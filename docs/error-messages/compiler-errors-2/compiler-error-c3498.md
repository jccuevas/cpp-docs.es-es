---
title: Error del compilador C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: ca9e2d272a5e9ab8fd69094bc1633dbd6ea2c3e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624706"
---
# <a name="compiler-error-c3498"></a>Error del compilador C3498

'var': no se puede capturar una variable que tiene un tipo administrado o WinRTtype

No se puede capturar una variable que tiene un tipo administrado o un tipo de Windows Runtime en una expresión lambda.

### <a name="to-correct-this-error"></a>Para corregir este error

- Pase la variable administrada o de Windows Runtime a la lista de parámetros de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3498 porque una variable que tiene un tipo administrado aparece en la lista de captura de una expresión lambda:

```
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente resuelve C3498 al pasar la variable administrada `s` a la lista de parámetros de la expresión lambda:

```
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
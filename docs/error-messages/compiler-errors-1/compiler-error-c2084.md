---
title: Error del compilador C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 881ae051b2779fe674b31b64a7cbe7be7cf63705
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757896"
---
# <a name="compiler-error-c2084"></a>Error del compilador C2084

la función '*function*' ya tiene un cuerpo

La función ya se ha definido.

Antes de Visual Studio 2002,

- El compilador aceptaría varias especializaciones de plantilla que se resolvieron en el mismo tipo real, aunque las definiciones adicionales nunca estarán disponibles. El compilador ahora detecta estas definiciones múltiples.

- `__int32` y `int` se tratan como tipos independientes. Ahora, el compilador trata `__int32` como sinónimo de `int`. Esto significa que el compilador detecta varias definiciones si una función está sobrecargada en `__int32` y `int` y produce un error.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Para corregir este error, quite la definición duplicada:

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```

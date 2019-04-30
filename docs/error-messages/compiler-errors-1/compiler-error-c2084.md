---
title: Error del compilador C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 9aaf3a88e63234dfb842e4b48afd6e55595e96ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391925"
---
# <a name="compiler-error-c2084"></a>Error del compilador C2084

función '*función*' ya tiene un cuerpo

La función ya se ha definido.

En las versiones de Visual C++ antes de Visual Studio 2002,

- El compilador aceptaban varias especializaciones de plantilla que se resuelven en el mismo tipo real, aunque las definiciones adicionales nunca estarían disponibles. Ahora, el compilador detecta estas definiciones múltiples.

- `__int32` y `int` se tratan como tipos distintos. El compilador trata ahora `__int32` como sinónimo de `int`. Esto significa que el compilador detecta varias definiciones si una función está sobrecargada en ambos `__int32` y `int` y produce un error.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Para corregir este error, quite la definición duplicada:

```
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
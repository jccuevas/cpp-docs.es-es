---
title: Error del compilador C2084 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09ce703b6908257e37c2b7ff1b2714f1426f941f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052119"
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
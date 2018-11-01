---
title: Error del compilador C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 9dfdee155e85bd772ed1d4ce22c525f8a4c79f5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458752"
---
# <a name="compiler-error-c3551"></a>Error del compilador C3551

"se espera un tipo de valor devuelto especificado en tiempo de ejecución"

Si utiliza la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. En el ejemplo siguiente, el tipo de valor devuelto especificado en tiempo de ejecución de la función `myFunction` es un puntero a una matriz de cuatro elementos de tipo `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Vea también

[auto](../../cpp/auto-cpp.md)
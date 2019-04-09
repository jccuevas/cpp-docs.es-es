---
title: Error del compilador C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 48b378eb734c5830bedbf417d99d34955e2e6d0f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023274"
---
# <a name="compiler-error-c3551"></a>Error del compilador C3551

"se espera un tipo de valor devuelto especificado en tiempo de ejecución"

Si utiliza la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. En el ejemplo siguiente, el tipo de valor devuelto especificado en tiempo de ejecución de la función `myFunction` es un puntero a una matriz de cuatro elementos de tipo `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Vea también

[auto](../../cpp/auto-cpp.md)
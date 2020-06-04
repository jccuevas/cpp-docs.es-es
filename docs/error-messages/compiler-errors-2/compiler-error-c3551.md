---
title: Error del compilador C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: e9a4ce2276a602d59e495a2f336bb9d59dc0cc99
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200764"
---
# <a name="compiler-error-c3551"></a>Error del compilador C3551

"se espera un tipo de valor devuelto especificado en tiempo de ejecución"

Si usa la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. En el ejemplo siguiente, el tipo de valor devuelto especificado en tiempo de ejecución de la función `myFunction` es un puntero a una matriz de cuatro elementos de tipo `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Consulte también

[auto](../../cpp/auto-cpp.md)

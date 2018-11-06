---
title: Error del compilador C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 90f6000c7d4c4bfa0d610bd5942df0b958e47c60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643634"
---
# <a name="compiler-error-c3530"></a>Error del compilador C3530

'auto' no se puede combinar con ningún otro especificador de tipo

Un especificador de tipo se usa con el `auto` palabra clave.

### <a name="to-correct-this-error"></a>Para corregir este error

1. No use un especificador de tipo en una declaración de variable que usa el `auto` palabra clave.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3530 porque variable `x` se declara con ambos el `auto` palabra clave y tipo `int`, y dado que el ejemplo se compila con **/Zc: Auto**.

```
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)
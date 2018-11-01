---
title: Error del compilador C2430
ms.date: 11/04/2016
f1_keywords:
- C2430
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
ms.openlocfilehash: 754758e652539e4f2d9b12e568b8ef5ccf41d8db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676478"
---
# <a name="compiler-error-c2430"></a>Error del compilador C2430

registrar más de un índice en 'identifier'

Se escala a más de un registro. El compilador admite la indización de escalado, pero solo puede escalar un registro.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2430.

```
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```
---
title: Error del compilador C3531 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3531
dev_langs:
- C++
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 375eb419e3f2f492df328a964eeb1bb77bc0d5dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106856"
---
# <a name="compiler-error-c3531"></a>Error del compilador C3531

'símbolo': un símbolo cuyo tipo contiene 'auto' debe tener un inicializador

La variable especificada no tiene una expresión de inicializador.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Especifique una expresión de inicializador, como una asignación simple que usa la sintaxis de signo igual, al declarar la variable.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3531 porque las variables `x1`, `y1, y2, y3`, y `z2` no se ha inicializado.

```
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)
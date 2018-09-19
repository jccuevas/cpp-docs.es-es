---
title: Compilador advertencia (nivel 3) C4390 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83131119e360bcf8193c2d6c8ca5a3cd09341516
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054199"
---
# <a name="compiler-warning-level-3-c4390"></a>Advertencia del compilador (nivel 3) C4390

';': una se encuentra; de instrucción controlada vacía ¿Esto es la intención?

Se encontró un punto y coma después de una instrucción de control que no contiene instrucciones.

Si obtiene C4390 debido a una macro, debe usar el [advertencia](../../preprocessor/warning.md) pragma para deshabilitar C4390 en el módulo que contiene la macro.

El ejemplo siguiente genera C4390:

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
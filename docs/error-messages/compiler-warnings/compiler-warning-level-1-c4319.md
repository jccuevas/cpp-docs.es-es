---
title: Compilador advertencia (nivel 1) C4319 | Documentos de Microsoft
ms.custom: 
ms.date: 1/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a492194003a639f684e84d125450067cd425276
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4319"></a>Advertencia del compilador (nivel 1) C4319

> ' ~': extensión de cero '*type1*'to'*type2*' de mayor tamaño

El resultado de la  **~**  (complemento bit a bit) (operador) es sin signo y, a continuación, ceros cuando se convierte a un tipo mayor.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, `~(a - 1)` se evalúa como una expresión de tipo long sin signo de 32 bits y, a continuación, se convierte a 64 bits mediante extensión con ceros. Esto podría producir resultados de operación inesperados.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```

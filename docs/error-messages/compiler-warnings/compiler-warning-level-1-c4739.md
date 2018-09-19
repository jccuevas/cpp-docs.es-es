---
title: Del compilador (nivel 1) de la advertencia C4739 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4739
dev_langs:
- C++
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7beaaca5d5791079fd8ea1ff8764f0b721f8d57d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112400"
---
# <a name="compiler-warning-level-1-c4739"></a>Advertencia del compilador (nivel 1) C4739

la referencia a la variable 'var' supera su espacio de almacenamiento

Se asignó un valor a una variable, pero el valor es mayor que el tamaño de la variable. La memoria se escribirá sobrepasando la ubicación de memoria de la variable y podrían perderse datos.

Para resolver esta advertencia, solo tiene que asignar un valor a una variable cuyo tamaño sea suficiente para dar cabida al valor.

El ejemplo siguiente genera la advertencia C4739:

```
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```
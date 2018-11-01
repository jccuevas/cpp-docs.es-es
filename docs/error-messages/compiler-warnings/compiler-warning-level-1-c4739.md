---
title: Advertencia del compilador (nivel 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 4c48ad9349361324c18ec790c51d1095cce104e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622097"
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
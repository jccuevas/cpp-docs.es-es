---
title: Advertencia del compilador (nivel 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: df8f3bcf6cfcc9feb2a400526285ccd9cb0396e4
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052417"
---
# <a name="compiler-warning-level-1-c4739"></a>Advertencia del compilador (nivel 1) C4739

la referencia a la variable 'var' supera su espacio de almacenamiento

Se asignó un valor a una variable, pero el valor es mayor que el tamaño de la variable. La memoria se escribirá sobrepasando la ubicación de memoria de la variable y podrían perderse datos.

Para resolver esta advertencia, solo tiene que asignar un valor a una variable cuyo tamaño sea suficiente para dar cabida al valor.

El ejemplo siguiente genera la advertencia C4739:

```cpp
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
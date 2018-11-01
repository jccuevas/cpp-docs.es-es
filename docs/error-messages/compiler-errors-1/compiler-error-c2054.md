---
title: Error del compilador C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: 7366995f8930b4733ccff73aef38ebcf65a0c120
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575661"
---
# <a name="compiler-error-c2054"></a>Error del compilador C2054

se esperaba ' (' seguir 'identifier'

Identificador de la función se utiliza en un contexto que requiere paréntesis.

Este error puede deberse a que si se omite un signo igual (=) en una inicialización compleja.

El ejemplo siguiente genera C2054:

```
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

Posible resolución:

```
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
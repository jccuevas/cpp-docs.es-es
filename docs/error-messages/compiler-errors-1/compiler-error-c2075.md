---
title: Error del compilador C2075
ms.date: 11/04/2016
f1_keywords:
- C2075
helpviewer_keywords:
- C2075
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
ms.openlocfilehash: 630c5cf2e90ae3373ef28b1388f06cd3fc069425
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302008"
---
# <a name="compiler-error-c2075"></a>Error del compilador C2075

'identificador': la inicialización de matriz necesita llaves.

No había llaves alrededor del inicializador de matriz especificado.

El ejemplo siguiente genera la advertencia C2075:

```c
// C2075.c
int main() {
   int i[] = 1, 2, 3 };   // C2075
}
```

Solución posible:

```c
// C2075b.c
int main() {
   int j[] = { 1, 2, 3 };
}
```

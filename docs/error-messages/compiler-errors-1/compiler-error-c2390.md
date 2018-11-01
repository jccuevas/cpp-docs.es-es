---
title: Error del compilador C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 89f6ebb02326413e8dca67d333e555321da4e645
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595878"
---
# <a name="compiler-error-c2390"></a>Error del compilador C2390

'identifier': clase de almacenamiento incorrecta 'especificador'

La clase de almacenamiento no es válida para el identificador de ámbito global. La clase de almacenamiento predeterminada se utiliza en lugar de la clase no válida.

Soluciones posibles:

- Si el identificador es una función, declárelo con `extern` almacenamiento.

- Si el identificador es un parámetro formal o una variable local, declárelo con almacenamiento automático.

- Si el identificador es una variable global, declárelo con ninguna clase de almacenamiento (almacenamiento automático).

## <a name="example"></a>Ejemplo

- El ejemplo siguiente genera C2390:

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```
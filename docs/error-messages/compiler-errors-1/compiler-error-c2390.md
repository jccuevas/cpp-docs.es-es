---
title: Error del compilador C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 515e2e151d27dd2eb84fc1dc71b9197b36b14cbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745049"
---
# <a name="compiler-error-c2390"></a>Error del compilador C2390

' Identifier ': clase de almacenamiento incorrecta ' Specifier '

La clase de almacenamiento no es válida para el identificador de ámbito global. La clase de almacenamiento predeterminada se usa en lugar de la clase no válida.

Soluciones posibles:

- Si el identificador es una función, declárelo con `extern` almacenamiento.

- Si el identificador es un parámetro formal o una variable local, declárelo con el almacenamiento automático.

- Si el identificador es una variable global, declárelo sin la clase de almacenamiento (almacenamiento automático).

## <a name="example"></a>Ejemplo

- En el ejemplo siguiente se genera C2390:

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```

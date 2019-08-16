---
title: Error del compilador C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: d48806982bbb6cdda4d29e47f6692e7e3601d6de
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503209"
---
# <a name="compiler-error-c2362"></a>Error del compilador C2362

> inicialización de '*identificador*' se omite en ' goto *etiqueta*'

Al compilar con [/Za](../../build/reference/za-ze-disable-language-extensions.md), un salto a la etiqueta impide que el identificador que se está inicializando.

Solo puede ir más allá de una declaración con un inicializador de si la declaración está incluida en un bloque que no está especificado, o si ya se ha inicializado la variable.

El ejemplo siguiente genera C2362:

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Posible resolución:

```cpp
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```
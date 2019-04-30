---
title: Error del compilador C2362
ms.date: 11/04/2016
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 17656b2a48a3680a9269d3ca300fd4188eda6b84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364329"
---
# <a name="compiler-error-c2362"></a>Error del compilador C2362

inicialización de 'identificador' se omite en 'goto label'

Cuando se compila con [/Za](../../build/reference/za-ze-disable-language-extensions.md), saltar a la etiqueta impide que el identificador que se está inicializando.

No se puede saltar una declaración con un inicializador a menos que la declaración está incluida en un bloque que no se ha especificado o ya se inicializó la variable.

El ejemplo siguiente genera la advertencia C2326:

```
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Posible resolución:

```
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
---
title: Error del compilador C2362 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2362
dev_langs:
- C++
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f78b850f95614255fed372570742a0f88a9e30e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035986"
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
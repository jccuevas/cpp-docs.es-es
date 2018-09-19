---
title: Compilador advertencia (nivel 1) C4142 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 011f71c1d57f03c2be9bac3df67cd0ed90aa8017
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117392"
---
# <a name="compiler-warning-level-1-c4142"></a>Compilador advertencia (nivel 1) C4142

¡¡¡Redefinición benigno de tipo

Se vuelve a definir un tipo de forma que no tiene ningún efecto en el código generado.

Posibles causas del error:

- Una función miembro de una clase derivada tiene un tipo de valor devuelto diferente de la función miembro correspondiente de la clase base.

- Un tipo definido con el `typedef` se vuelve a definir comandos con una sintaxis diferente.

El ejemplo siguiente genera C4142:

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```
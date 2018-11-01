---
title: Compilador advertencia (nivel 1) C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: bfe54fc40b4d6927a1d75f529ec9b619f9b29226
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490524"
---
# <a name="compiler-warning-level-1-c4028"></a>Compilador advertencia (nivel 1) C4028

'número' distinto de la declaración de parámetros formales

El tipo del parámetro formal no coincide con el parámetro correspondiente en la declaración. Se utiliza el tipo en la declaración original.

Esta advertencia sólo es válida para el código fuente de C.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4028.

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```
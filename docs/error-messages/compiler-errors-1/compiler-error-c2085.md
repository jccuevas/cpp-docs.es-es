---
title: Error del compilador C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: a65e3c0ea622950b99b9ba83fc168b4718d13e46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560165"
---
# <a name="compiler-error-c2085"></a>Error del compilador C2085

'identifier': no en la lista de parámetros formales

El identificador se ha declarado en una definición de función, pero no en la lista de parámetros formales. (Sólo en ANSI C)

El ejemplo siguiente genera C2085:

```
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Posible resolución:

```
// C2085b.c
void func1( void );
int main( void ) {}
```

Con el punto y coma que falta, `func1()` parece una definición de función, no un prototipo, por lo que `main` se define dentro de `func1()`, Error C2085 para identificador `main`.
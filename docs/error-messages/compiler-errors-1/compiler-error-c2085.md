---
title: Error del compilador C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 7dbf7266a6330a1fdb46d7f2df90e7684f026d9a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301969"
---
# <a name="compiler-error-c2085"></a>Error del compilador C2085

' Identifier ': no está en la lista de parámetros formales

El identificador se declaró en una definición de función, pero no en la lista de parámetros formales. (Solo ANSI C)

En el ejemplo siguiente se genera C2085:

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Solución posible:

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

Con el punto y coma que falta, `func1()` se parece a una definición de función, no a un prototipo, por lo que `main` se define dentro de `func1()`y genera el error C2085 para el identificador `main`.

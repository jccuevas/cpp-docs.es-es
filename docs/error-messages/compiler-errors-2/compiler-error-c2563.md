---
title: Error del compilador C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 04a10c82fa6aa39bcf1098d6d4aabfc2f769e7c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539313"
---
# <a name="compiler-error-c2563"></a>Error del compilador C2563

Error de coincidencia en la lista de parámetros formales

La lista de parámetros formales de una función (o un puntero a una función) no coincide con los de otra función (o puntero a una función miembro). Como resultado, no se realizó la asignación de funciones o punteros.

El ejemplo siguiente genera C2563:

```
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```
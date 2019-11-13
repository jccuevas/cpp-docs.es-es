---
title: ADVERTENCIA del compilador (nivel 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: d7c8cee42f17ad3301980852b8333ea37f5ca6be
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051783"
---
# <a name="compiler-warning-level-3-c4197"></a>ADVERTENCIA del compilador (nivel 3) C4197

' type ': se omite volatile de nivel superior en la conversión

El compilador detectó una conversión a un tipo de valor r que está calificado con [volatile](../../cpp/volatile-cpp.md), o una conversión de un tipo de valor r a algún tipo que está calificado con volatile. Según el estándar de C (6.5.3), las propiedades asociadas a tipos calificados solo son significativas para las expresiones de valor l.

En el ejemplo siguiente se genera C4197:

```cpp
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}
```
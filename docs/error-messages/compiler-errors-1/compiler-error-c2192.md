---
title: Error del compilador C2192
ms.date: 11/04/2016
f1_keywords:
- C2192
helpviewer_keywords:
- C2192
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
ms.openlocfilehash: 3285221089c2a1ed61b03572ed8915ebfbb00e48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444257"
---
# <a name="compiler-error-c2192"></a>Error del compilador C2192

declaración de parámetro 'número' diferente

Una función de C se ha declarado una segunda vez con una lista de parámetros distinta. C no admite funciones sobrecargadas.

El ejemplo siguiente genera C2192:

```
// C2192.c
// compile with: /Za /c
void func( float, int );
void func( int, float );   // C2192, different parameter list
void func2( int, float );   // OK
```
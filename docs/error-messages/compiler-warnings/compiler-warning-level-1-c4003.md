---
title: Compilador advertencia (nivel 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 7b1b87c643111f2b12124e348be8fb823e113937
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653159"
---
# <a name="compiler-warning-level-1-c4003"></a>Compilador advertencia (nivel 1) C4003

no hay suficientes parámetros reales para la macro 'identificador'

El número de parámetros formales de la definición de macro supera el número de parámetros reales de la macro. Expansión de macro reemplaza el texto vacío para los parámetros que faltan.

El ejemplo siguiente genera C4003:

```
// C4003.cpp
// compile with: /WX
#define test(a,b) (a+b)

int main()
{
   int a = 1;
   int b = 2;
   a = test(b);   // C4003
   // try..
   a = test(a,b);
}
```
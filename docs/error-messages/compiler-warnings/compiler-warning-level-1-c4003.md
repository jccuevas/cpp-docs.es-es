---
title: ADVERTENCIA del compilador (nivel 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 4adbffe3220060ee9d43f01cf94628f85d3991cc
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627385"
---
# <a name="compiler-warning-level-1-c4003"></a>ADVERTENCIA del compilador (nivel 1) C4003

no hay suficientes parámetros reales para la macro 'identificador'

El número de parámetros formales en la definición de macro supera el número de parámetros reales de la macro. La expansión de macro sustituye el texto vacío de los parámetros que faltan.

En el ejemplo siguiente se genera C4003:

```cpp
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
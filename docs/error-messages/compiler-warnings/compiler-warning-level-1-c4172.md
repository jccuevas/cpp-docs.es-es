---
title: Del compilador (nivel 1) de la advertencia C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: caa71da9182c1da1d17d87d901084d0ee9badf73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536629"
---
# <a name="compiler-warning-level-1-c4172"></a>Del compilador (nivel 1) de la advertencia C4172

devolución de dirección de variable local o temporal

Una función devuelve la dirección de un objeto temporal o variable local. Objetos temporales y variables locales se destruyen cuando se devuelve una función, por lo que la dirección devuelta no es válida.

Vuelva a diseñar la función para que no devuelve la dirección de un objeto local.

El ejemplo siguiente genera C4172:

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```
---
title: Error del compilador C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 516f9b024947e0100a753e4e010a5b51b1fb24a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230534"
---
# <a name="compiler-error-c2466"></a>Error del compilador C2466

no se puede asignar una matriz de tamaño constante 0

Una matriz es asignada o puede declarar con tamaño cero. La expresión constante para el tamaño de la matriz debe ser un entero mayor que cero. Una declaración de matriz con un subíndice cero es válida sólo para una clase, estructura o miembro de unión y sólo con las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

El ejemplo siguiente genera C2466:

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
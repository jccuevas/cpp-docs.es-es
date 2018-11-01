---
title: Error del compilador C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: b45ec25f1ed516ae73b242fdcc7c66f68c92f724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624723"
---
# <a name="compiler-error-c2040"></a>Error del compilador C2040

'operador': 'identificador1' se diferencia del 'identificador2' en los niveles de direccionamiento indirecto

Una expresión que contenga los operandos especificados tiene tipos de operando incompatibles o tipos de operando convertidos de forma implícita. Si ambos operandos son aritméticos o ninguno de ellos lo es (por ejemplo, una matriz o puntero), se usan sin cambios. Si uno de los operandos es aritmético y el otro no, el operador aritmético se convierte al tipo del operando no aritmético.

Este ejemplo genera el error C2040 y muestra cómo corregirlo.

```
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```
---
title: Advertencia del compilador (nivel 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: c18dbac0681067d9bc52455dfdbe44a24c786ee7
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051542"
---
# <a name="compiler-warning-level-1-c4807"></a>Advertencia del compilador (nivel 1) C4807

'operation': combinación no segura del tipo 'type' y el campo de bits con signo de tipo 'type'

Esta advertencia se genera al comparar un campo de bits con signo de un bit con una variable `bool` . Puesto que el campo de bits con signo de un bit solo puede contener los valores -1 o 0, es arriesgado compararlo con `bool`. No se generan advertencias con la mezcla de `bool` y campos de bits sin signo de un bit, ya que son idénticas a `bool` y solo pueden contener 0 o 1.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4807:

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
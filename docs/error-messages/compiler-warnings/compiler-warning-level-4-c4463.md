---
title: Del compilador (nivel 4) de la advertencia C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: e125a532f87533958ec43ed5580665ad4108856b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474833"
---
# <a name="compiler-warning-level-4-c4463"></a>Del compilador (nivel 4) de la advertencia C4463

> desbordamiento; asignar *valor* al campo de bits que solo puede contener valores de *low_value* a *high_value*

Asignado *valor* está fuera del intervalo de valores que puede contener el campo de bits. Tipos de campo de bits con signo usan orden superior de bits para el inicio de sesión, por lo que si *n* es el tamaño de campo de bits, el intervalo de campos de bits con signo es -2<sup>n-1</sup> a 2<sup>n-1</sup>-1, aunque sin signo campos de bits tienen un intervalo de 0 a 2<sup>n</sup>-1.

## <a name="example"></a>Ejemplo

En este ejemplo genera C4463 porque intenta asignar un valor de 3 a un campo de bits de tipo `int` con un tamaño de 2, que tiene un intervalo de -2 a 1.

Para corregir este problema, puede cambiar el valor asignado a algo en el intervalo permitido. Si el campo de bits está destinado a contener los valores sin signo en el intervalo comprendido entre 0 y 3, puede cambiar el tipo de declaración para `unsigned`. Si el campo está destinado a contener los valores en el intervalo -4 a 3, puede cambiar el tamaño del campo de bits a 3.

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```

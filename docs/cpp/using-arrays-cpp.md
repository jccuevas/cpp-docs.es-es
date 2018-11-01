---
title: Utilizar matrices (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
ms.openlocfilehash: 7f7a987a2b4c18e59dd058ccfc4375c304188398
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575518"
---
# <a name="using-arrays-c"></a>Utilizar matrices (C++)

Se puede obtener acceso a los elementos individuales de una matriz mediante el operador de subíndice de matriz (`[ ]`). Si se utiliza una matriz unidimensional en una expresión que no tiene subíndice, el nombre de la matriz se evalúa como un puntero al primer elemento de la matriz.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Cuando se utilizan matrices multidimensionales, se pueden emplear varias combinaciones en las expresiones.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

En el código anterior, `multi` es una matriz tridimensional de tipo **doble**. El `p2multi` puntero apunta a una matriz de tipo **doble** de tamaño tres. En este ejemplo, la matriz se utiliza con uno, dos y tres subíndices. Aunque es más frecuente especificar todos los subíndices, como en la instrucción `cout`, a veces es útil seleccionar un subconjunto concreto de elementos de la matriz, como se muestra en las instrucciones que hay después de `cout`.

## <a name="see-also"></a>Vea también

[Matrices](../cpp/arrays-cpp.md)
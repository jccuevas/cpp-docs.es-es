---
title: Instrucción for basada en intervalo (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 504f177cf68b978642f15ba4799cab8cb517f447
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188355"
---
# <a name="range-based-for-statement-c"></a>Instrucción for basada en intervalo (C++)

Ejecuta `statement` de forma repetida y secuencial para cada elemento de `expression`.

## <a name="syntax"></a>Sintaxis

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>Observaciones

Use la instrucción **for** basada en intervalo para construir bucles que se deben ejecutar a través de un "intervalo", que se define como todo lo que se puede recorrer en iteración; por ejemplo C++ , `std::vector`o cualquier otra secuencia de la biblioteca estándar cuyo intervalo esté definido por un `begin()` y `end()`. El nombre que se declara en la parte `for-range-declaration` es local para la instrucción **for** y no se puede volver a declarar en `expression` o `statement`. Tenga en cuenta que se prefiere la palabra clave [auto](../cpp/auto-cpp.md) en la parte `for-range-declaration` de la instrucción.

**Novedades de Visual Studio 2017:**  Los bucles for basados en intervalos ya no requieren que Begin () y end () devuelvan objetos del mismo tipo. Esto permite que end() devuelva un objeto centinela como el usado por los intervalos tal como se define en la propuesta de intervalos V3. Para más información, vea [Generalizing the Range-Based For Loop](https://wg21.link/p0184r0) (Generalización del bucle for basado en intervalos) y [range-v3 library](https://github.com/ericniebler/range-v3) (Biblioteca range-v3) en GitHub.

Este código muestra cómo usar bucles **for** basados en intervalos para recorrer en iteración una matriz y un vector:

```cpp
// range-based-for.cpp
// compile by using: cl /EHsc /nologo /W4
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    // Basic 10-element integer array.
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Range-based for loop to iterate through the array.
    for( int y : x ) { // Access by value using a copy declared as a specific type.
                       // Not preferred.
        cout << y << " ";
    }
    cout << endl;

    // The auto keyword causes type inference to be used. Preferred.

    for( auto y : x ) { // Copy of 'x', almost always undesirable
        cout << y << " ";
    }
    cout << endl;

    for( auto &y : x ) { // Type inference by reference.
        // Observes and/or modifies in-place. Preferred when modify is needed.
        cout << y << " ";
    }
    cout << endl;

    for( const auto &y : x ) { // Type inference by const reference.
        // Observes in-place. Preferred when no modify is needed.
        cout << y << " ";
    }
    cout << endl;
    cout << "end of integer array test" << endl;
    cout << endl;

    // Create a vector object that contains 10 elements.
    vector<double> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i + 0.14159);
    }

    // Range-based for loop to iterate through the vector, observing in-place.
    for( const auto &j : v ) {
        cout << j << " ";
    }
    cout << endl;
    cout << "end of vector test" << endl;
}
```

Este es el resultado:

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

Un bucle **for** basado en intervalo finaliza cuando se ejecuta uno de estos en `statement`: [break](../cpp/break-statement-cpp.md), [Return](../cpp/return-statement-cpp.md)o [goto](../cpp/goto-statement-cpp.md) a una instrucción con etiqueta fuera del bucle **for** basado en intervalo. Una instrucción [continue](../cpp/continue-statement-cpp.md) en un bucle **for** basado en intervalo finaliza solo la iteración actual.

Tenga en cuenta que estos datos están basados en intervalos **para**:

- Reconoce automáticamente las matrices.

- Reconoce los contenedores que tienen `.begin()` y `.end()`.

- Utiliza la búsqueda dependiente de argumentos `begin()` y `end()` para todo lo demás.

## <a name="see-also"></a>Consulte también

[auto](../cpp/auto-cpp.md)<br/>
[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[while (Instrucción) (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while (Instrucción) (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for (Instrucción) (C++)](../cpp/for-statement-cpp.md)

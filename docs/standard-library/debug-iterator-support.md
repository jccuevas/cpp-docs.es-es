---
title: Compatibilidad de los iteradores de depuración | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffcd69475d13277884deaf9ee114f3cd8d86516f
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601475"
---
# <a name="debug-iterator-support"></a>Debug Iterator Support

La biblioteca en tiempo de ejecución de Visual C++ detecta un uso incorrecto del iterador, valida y muestra un cuadro de diálogo en tiempo de ejecución. Para habilitar la compatibilidad con el iterador de depuración, debe usar versiones de depuración de la biblioteca estándar de C++ y la biblioteca en tiempo de ejecución de C para compilar el programa. Para obtener más información, vea [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md). Para obtener información sobre cómo usar iteradores comprobados, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

El estándar de C++ describe cómo las funciones miembro pueden provocar que los iteradores de un contenedor se conviertan en no válidos. Dos ejemplos son:

- Borrar un elemento de un contenedor hace que los iteradores del elemento sean no válidos.

- Aumentar el tamaño de un [vector](../standard-library/vector.md) mediante inserción causa que los iteradores de `vector` no sean válidos.

## <a name="invalid-iterators"></a>Iteradores no válidos

Si compila este programa de ejemplo en modo de depuración, en tiempo de ejecución se valida y finaliza.

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v {10, 15, 20};
   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="using-iteratordebuglevel"></a>Uso de _ITERATOR_DEBUG_LEVEL

Puede usar la macro de preprocesador [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) para desactivar la característica de depuración de iteradores en una compilación de depuración. Este programa no valida, pero aún desencadena un comportamiento indefinido.

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v {10, 15, 20};

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

```Output
20
-572662307
```

## <a name="unitialized-iterators"></a>Iteradores no inicializados

También se produce una aserción si intenta usar un iterador antes de que se inicialice, como se muestra aquí:

```cpp
// iterator_debugging_2.cpp
// compile by using: /EHsc /MDd
#include <string>
using namespace std;

int main() {
   string::iterator i1, i2;
   if (i1 == i2)
      ;
}
```

## <a name="incompatible-iterators"></a>Iteradores incompatibles

En el ejemplo de código siguiente se produce una aserción porque los dos iteradores del algoritmo [for_each](../standard-library/algorithm-functions.md#for_each) son incompatibles. Comprobación de algoritmos para determinar si los iteradores que se les suministran hacen referencia al mismo contenedor.

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1 {10, 20};
    vector<int> v2 {10, 20};

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

Tenga en cuenta que este ejemplo usa la expresión lambda `[] (int& elem) { elem *= 2; }` en lugar de un functor. Aunque esta opción no influye en el error de aserción (un functor similar provocaría el mismo error), las expresiones lambda son una forma muy útil de realizar tareas de objeto de función compacta. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="iterators-going-out-of-scope"></a>Iteradores va fuera del ámbito

Comprobaciones de iteradores de depuración también provocar una variable de iterador que se declara en un **para** bucle esté fuera de ámbito cuando el **para** finaliza el ámbito de bucle.

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v {10, 15, 20};

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="destructors-for-debug-iterators"></a>Destructores para los iteradores de depuración

Los iteradores de depuración tienen destructores no triviales. Si no se ejecuta un destructor, pero se libera la memoria del objeto, pueden producirse daños en datos y las infracciones de acceso. Considere este ejemplo:

```cpp
// iterator_debugging_5.cpp
// compile by using: /EHsc /MDd
#include <vector>
struct base {
   // TO FIX: uncomment the next line
   // virtual ~base() {}
};

struct derived : base {
   std::vector<int>::iterator m_iter;
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}
   ~derived() {}
};

int main() {
  auto vect = std::vector<int>(10);
  auto sink = new auto(std::begin(vect));
  ::operator delete(sink); // frees the memory without calling ~iterator()
} // access violation
```

## <a name="see-also"></a>Vea también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>

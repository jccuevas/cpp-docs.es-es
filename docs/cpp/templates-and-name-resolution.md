---
title: Plantillas y resolución de nombres
ms.date: 11/04/2016
ms.assetid: 519ba7b5-cd25-4549-865a-9a7b9dffdc28
ms.openlocfilehash: e4a53df0a192c1d7b7f376e4401eb99fcbf7d481
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266756"
---
# <a name="templates-and-name-resolution"></a>Plantillas y resolución de nombres

En las definiciones de plantilla, hay tres tipos de nombres.

- Nombres declarados localmente, como el nombre de la propia plantilla y cualquier nombre declarado dentro de la definición de plantilla.

- Nombres del ámbito de inclusión fuera de la definición de plantilla.

- Nombres que dependen de alguna manera de los argumentos de plantilla, denominados nombres dependientes.

Mientras que los dos primeros nombres pertenecen también a ámbitos de clase y función, en las definiciones de plantillas se requieren reglas especiales de resolución de nombres para tratar la complejidad agregada de los nombres dependientes. Esto se debe a que el compilador apenas tiene conocimiento de estos nombres hasta que se crea una instancia de la plantilla, ya que pueden ser tipos totalmente diferentes en función de los argumentos de plantilla que se usen. Los nombres no dependientes se buscan de acuerdo con las reglas habituales y en el punto de definición de la plantilla. Estos nombres, que son independientes de los argumentos de plantilla, se buscan una sola vez para todas las especializaciones de plantilla. Los nombres dependientes no se buscan hasta que se crea una instancia de la plantilla y se buscan por separado para cada especialización.

Un tipo es dependiente si depende de los argumentos de plantilla. En concreto, un tipo es dependiente si es:

- El propio argumento de plantilla:

    ```cpp
    T
    ```

- Un nombre completo con una clasificación que incluye un tipo dependiente:

    ```cpp
    T::myType
    ```

- Un nombre completo si la parte incompleta identifica un tipo dependiente:

    ```cpp
    N::T
    ```

- Un tipo const o volatile para el que el tipo base es un tipo dependiente:

    ```cpp
    const T
    ```

- Un tipo de puntero, referencia, matriz o puntero de función basado en un tipo dependiente:

    ```cpp
    T *, T &, T [10], T (*)()
    ```

- Una matriz cuyo tamaño se basa en un parámetro de plantilla:

    ```cpp
    template <int arg> class X {
    int x[arg] ; // dependent type
    }
    ```

- Un tipo de plantilla creado a partir de un parámetro de plantilla:

    ```cpp
    T<int>, MyTemplate<T>
    ```

## <a name="type-dependence-and-value-dependence"></a>Dependencia de tipos y dependencia de valores

Los nombres y las expresiones dependientes de un parámetro de plantilla se clasifican como dependientes del tipo o dependientes del valor, en función de si el parámetro de plantilla es un parámetro de tipo o un parámetro de valor. Además, cualquier identificador declarado en una plantilla con un tipo dependiente del argumento de plantilla se considera dependiente del valor, como en el caso de un tipo de entero o de enumeración inicializado con una expresión dependiente del valor.

Las expresiones dependientes del tipo y dependientes del valor son expresiones que implican variables dependientes del tipo o dependientes del valor. Estas expresiones pueden tener una semántica diferente en función de los parámetros utilizados para la plantilla.

## <a name="see-also"></a>Vea también

[Templates](../cpp/templates-cpp.md) (Plantillas [C++])
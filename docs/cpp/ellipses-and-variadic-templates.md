---
title: Puntos suspensivos y plantillas variádicas
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 9c9294089b9f0a144946b7f6b81da2a71ca710bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189265"
---
# <a name="ellipses-and-variadic-templates"></a>Puntos suspensivos y plantillas variádicas

En este artículo se muestra cómo utilizar los puntos suspensivos (`...`) con plantillas variádicas de C++. Los puntos suspensivos han tenido muchos usos en C y C++. Entre ellos se incluyen listas de argumentos de variable para funciones. La función `printf()` de la biblioteca en tiempo de ejecución de C es uno de los ejemplos más conocidos.

Una *plantilla variádicas* es una plantilla de clase o de función que admite un número arbitrario de argumentos. Este mecanismo resulta especialmente útil para los desarrolladores de bibliotecas de C++, ya que puede aplicarse tanto a las plantillas de clase como a las plantillas de función y, por tanto, proporciona una gama amplia de funcionalidad y flexibilidad con seguridad de tipos y no triviales.

## <a name="syntax"></a>Sintaxis

Las plantillas variádicas utilizan los puntos suspensivos de dos maneras. A la izquierda del nombre del parámetro, significa un paquete de *parámetros*y, a la derecha del nombre del parámetro, expande los paquetes de parámetros en nombres independientes.

A continuación se muestra un ejemplo básico de sintaxis de definición de *clase de plantilla variádicas* :

```cpp
template<typename... Arguments> class classname;
```

Tanto en los paquetes de parámetros como en las expansiones se puede agregar espacio en blanco alrededor de los puntos suspensivos, según se desee, como se muestra en estos ejemplos:

```cpp
template<typename ...Arguments> class classname;
```

O bien:

```cpp
template<typename ... Arguments> class classname;
```

Tenga en cuenta que en este artículo se utiliza la convención que se muestra en el primer ejemplo (los puntos suspensivos van junto a `typename`).

En los ejemplos anteriores, *arguments* es un paquete de parámetros. La clase `classname` puede aceptar un número variable de argumentos, como en estos ejemplos:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

Cuando se usa una definición de clase de plantilla variádica, también puede ser necesario al menos un parámetro:

```cpp
template <typename First, typename... Rest> class classname;
```

A continuación se muestra un ejemplo básico de sintaxis de *función de plantilla variádicas* :

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

A continuación, el paquete de parámetros *arguments* se expande para su uso, como se muestra en la sección siguiente, **Descripción de las plantillas variádicas**.

Es posible utilizar otras formas de sintaxis de función de plantilla variática, incluidas las de estos ejemplos, entre otras:

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

También se permiten especificadores como **const** :

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Como ocurre con las definiciones de clase de plantilla variádica, se pueden crear funciones que requieran al menos un parámetro:

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Las plantillas variádicas utilizan el operador `sizeof...()` (relacionado con el anterior operador `sizeof()`):

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>Más información sobre la posición de los puntos suspensivos

Anteriormente en este artículo se ha descrito la posición de los puntos suspensivos que definen los paquetes de parámetros y las expansiones como "a la izquierda del nombre de parámetro, significa un paquete de parámetros, y a la derecha del nombre de parámetro, expande los paquetes de parámetros en nombres diferentes". Esto es técnicamente cierto pero puede ser confuso trasladarlo al código. Considere:

- En una lista de parámetros de plantilla (`template <parameter-list>`), `typename...` presenta un paquete de parámetros de plantilla.

- En una cláusula de declaración de parámetros (`func(parameter-list)`), los puntos suspensivos de "nivel superior" presentan un paquete de parámetros de función y la posición de los puntos suspensivos es importante:

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Cuando los puntos suspensivos aparecen inmediatamente después de un nombre de parámetro, tiene una expansión del paquete de parámetros.

## <a name="example"></a>Ejemplo

Una buena manera de mostrar el mecanismo de la función de plantilla variádica consiste en utilizarlo para reescribir cierta funcionalidad de `printf`:

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>Output

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
>  La mayoría de las implementaciones que incorporan funciones de plantilla variádicas utilizan la recursividad de alguna forma, pero es ligeramente diferente de la recursividad tradicional.  La recursividad tradicional conlleva una función que se llama a sí misma utilizando la misma firma. (Puede estar sobrecargado o con plantilla, pero se elige la misma firma cada vez). La recursividad variádicas implica llamar a una plantilla de función variádicas mediante el uso de números de argumentos diferentes (casi siempre en disminución) y, por lo tanto, marcan una firma diferente cada vez. Sigue siendo necesario un "caso base", pero la naturaleza de la recursividad es diferente.

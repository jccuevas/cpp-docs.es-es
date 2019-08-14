---
title: Archivos de encabezadoC++()
ms.date: 04/20/2018
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 98d37944f8c037f3ba25d80c7d35b3560ad11d40
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980472"
---
# <a name="header-files-c"></a>Archivos de encabezadoC++()

Los nombres de los elementos de programa, como variables, funciones, clases, etc., se deben declarar antes de que se puedan utilizar. Por ejemplo, no puede simplemente escribir `x = 42` sin declarar primero "x".

```cpp
int x; // declaration
x = 42; // use x
```

La declaración indica al compilador si el elemento es un **tipo int**, **Double**, una **función**, una **clase** u otra cosa.  Además, cada nombre se debe declarar (directa o indirectamente) en cada archivo. cpp en el que se usa. Al compilar un programa, cada archivo. cpp se compila de forma independiente en una unidad de compilación. El compilador no tiene conocimiento de los nombres que se declaran en otras unidades de compilación. Esto significa que si define una clase o una función o una variable global, debe proporcionar una declaración de ese elemento en cada archivo. cpp adicional que lo use. Cada declaración de ese elemento debe ser exactamente idéntica en todos los archivos. Una ligera incoherencia producirá errores, o un comportamiento no deseado, cuando el vinculador intente fusionar mediante combinación todas las unidades de compilación en un único programa.

Para minimizar la posibilidad de errores, C++ ha adoptado la Convención de usar *archivos de encabezado* para contener declaraciones. Las declaraciones se realizan en un archivo de encabezado y, a continuación, se usa la Directiva #include en todos los archivos. cpp u otro archivo de encabezado que requiera dicha declaración. La Directiva #include inserta una copia del archivo de encabezado directamente en el archivo. cpp antes de la compilación.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una manera común de declarar una clase y, a continuación, usarla en un archivo de código fuente diferente. Comenzaremos con el archivo de encabezado, `my_class.h`. Contiene una definición de clase, pero tenga en cuenta que la definición está incompleta. no se ha `do_something` definido la función miembro:

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

A continuación, cree un archivo de implementación (normalmente con una extensión. cpp o similar). Llamaremos al archivo my_class. cpp y proporcionaremos una definición para la declaración de miembro. Agregamos una `#include` Directiva para el archivo "my_class. h" para que la declaración my_class se inserte en este punto en el archivo. cpp y incluimos `<iostream>` la declaración de incorporación de cambios en `std::cout`la declaración de. Tenga en cuenta que las comillas se usan para los archivos de encabezado en el mismo directorio que el archivo de código fuente, y se usan corchetes angulares para los encabezados de la biblioteca estándar. Además, muchos encabezados de la biblioteca estándar no tienen. h ni cualquier otra extensión de archivo.

En el archivo de implementación, se puede usar opcionalmente una instrucción **using** para evitar tener que calificar cada mención de "my_class" o "cout" con "N::" o "STD::".  No incluya instrucciones **using** en los archivos de encabezado.

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

Ahora podemos usar `my_class` en otro archivo. cpp. #Include el archivo de encabezado para que el compilador Extraiga la declaración. Todo el compilador debe saber que my_class es una clase que tiene una función miembro pública denominada `do_something()`.

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

Una vez que el compilador termina de compilar cada archivo. cpp en archivos. obj, pasa los archivos. obj al enlazador. Cuando el vinculador combina los archivos objeto, encuentra exactamente una definición de my_class; está en el archivo. obj generado para my_class. cpp y la compilación se realiza correctamente.

## <a name="include-guards"></a>Incluir protecciones

Normalmente, los archivos de encabezado tienen una *protección* de `#pragma once` inclusión o una directiva para asegurarse de que no se insertan varias veces en un único archivo. cpp.

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>Qué se debe incluir en un archivo de encabezado

Dado que un archivo de encabezado podría estar incluido potencialmente en varios archivos, no puede contener definiciones que puedan generar varias definiciones del mismo nombre. Los siguientes elementos no están permitidos o se consideran muy incorrectos:

- definiciones de tipos integrados en un espacio de nombres o ámbito global
- definiciones de funciones no insertadas
- definiciones de variables no const
- definiciones de agregado
- espacios de nombres sin nombre
- Directivas using

El uso de la directiva **using** no producirá necesariamente un error, pero puede causar un problema porque pone el espacio de nombres en el ámbito de cada archivo. cpp que incluye directa o indirectamente ese encabezado.

## <a name="sample-header-file"></a>Archivo de encabezado de ejemplo

En el ejemplo siguiente se muestran los distintos tipos de declaraciones y definiciones que se permiten en un archivo de encabezado:

```cpp
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```

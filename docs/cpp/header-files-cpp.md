---
title: Archivos de encabezado (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 4ab6a2b2626cde94f35678bc9ec789b80d493b8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367240"
---
# <a name="header-files-c"></a>Archivos de encabezado (C++)

Los nombres de elementos de programa como variables, funciones, clases, etc. deben declararse antes de que se puedan utilizar. Por ejemplo, no puede `x = 42` escribir sin declarar primero 'x'.

```cpp
int x; // declaration
x = 42; // use x
```

La declaración indica al compilador si el elemento es un **int**, un **double**, una **función,** una **clase** o alguna otra cosa.  Además, cada nombre debe declararse (directa o indirectamente) en cada archivo .cpp en el que se utiliza. Al compilar un programa, cada archivo .cpp se compila de forma independiente en una unidad de compilación. El compilador no tiene conocimiento de qué nombres se declaran en otras unidades de compilación. Esto significa que si define una clase o función o variable global, debe proporcionar una declaración de ese objeto en cada archivo .cpp adicional que lo utilice. Cada declaración de esa cosa debe ser exactamente idéntica en todos los archivos. Una ligera incoherencia provocará errores, o un comportamiento no intencionado, cuando el vinculador intente combinar todas las unidades de compilación en un solo programa.

Para minimizar la posibilidad de errores, C++ ha adoptado la convención de usar archivos de *encabezado* para contener declaraciones. Las declaraciones se realizan en un archivo de encabezado y, a continuación, se usa la directiva #include en cada archivo .cpp u otro archivo de encabezado que requiera esa declaración. La directiva #include inserta una copia del archivo de encabezado directamente en el archivo .cpp antes de la compilación.

> [!NOTE]
> En Visual Studio 2019, la característica de *módulos* C++20 se presenta como una mejora y reemplazo final para los archivos de encabezado. Para obtener más información, consulte [Información general de los módulos en C++](modules-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una forma común de declarar una clase y, a continuación, usarla en un archivo de origen diferente. Comenzaremos con el archivo `my_class.h`de encabezado, . Contiene una definición de clase, pero tenga en cuenta que la definición está incompleta; la función `do_something` miembro no está definida:

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

A continuación, cree un archivo de implementación (normalmente con una extensión .cpp o similar). Llamaremos al archivo my_class.cpp y proporcionaremos una definición para la declaración de miembro. Agregamos `#include` una directiva para el archivo "my_class.h" con el fin de que la declaración `<iostream>` de my_class inserten en este momento en el archivo .cpp, e incluimos para extraer la declaración para `std::cout`. Tenga en cuenta que las comillas se utilizan para los archivos de encabezado en el mismo directorio que el archivo de origen, y los corchetes angulares se utilizan para los encabezados de biblioteca estándar. Además, muchos encabezados de biblioteca estándar no tienen .h ni ninguna otra extensión de archivo.

En el archivo de implementación, opcionalmente podemos usar una instrucción **using** para evitar tener que calificar cada mención de "my_class" o "cout" con "N::" o "std::".  ¡No **ponga** sin instrucciones using en los archivos de encabezado!

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

Ahora podemos `my_class` usar en otro archivo .cpp. Hemos #include el archivo de encabezado para que el compilador extraiga la declaración. Todo lo que el compilador necesita saber es que my_class `do_something()`es una clase que tiene una función miembro pública llamada .

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

Una vez que el compilador termina de compilar cada archivo .cpp en archivos .obj, pasa los archivos .obj al vinculador. Cuando el vinculador combina los archivos de objeto, encuentra exactamente una definición para my_class; se encuentra en el archivo .obj generado para my_class.cpp y la compilación se realiza correctamente.

## <a name="include-guards"></a>Incluir guardias

Normalmente, los archivos de encabezado `#pragma once` tienen una protección de *inclusión* o una directiva para asegurarse de que no se insertan varias veces en un único archivo .cpp.

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

## <a name="what-to-put-in-a-header-file"></a>Qué poner en un archivo de encabezado

Dado que varios archivos pueden incluir un archivo de encabezado, no puede contener definiciones que puedan generar varias definiciones del mismo nombre. No se permite lo siguiente, o se consideran muy malas prácticas:

- Definiciones de tipo integradas en el espacio de nombres o ámbito global
- definiciones de funciones no en línea
- definiciones de variables no const
- definiciones agregadas
- espacios de nombres sin nombre
- Directivas using

El uso de la directiva **using** no necesariamente provocará un error, pero puede provocar un problema porque pone el espacio de nombres en el ámbito de cada archivo .cpp que incluye directa o indirectamente ese encabezado.

## <a name="sample-header-file"></a>Archivo de encabezado de ejemplo

En el ejemplo siguiente se muestran los distintos tipos de declaraciones y definiciones que se permiten en un archivo de encabezado:

```cpp
// sample.h
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

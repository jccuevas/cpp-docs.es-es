---
title: Archivos de encabezado (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 04/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- header files [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b571cd2836e66ebef21898af27cf2a6d7082e0e5
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36261071"
---
# <a name="header-files-c"></a>Archivos de encabezado (C++)

Los nombres de elementos de programa, como variables, funciones, clases etc. deben declararse antes de que se puedan utilizar. Por ejemplo, no se puede escribir simplemente `x = 42` sin declararla primero 'x'. 

```cpp
int x; // declaration
x = 42; // use x
```

 La declaración indica al compilador si es un **int**, un **doble**, un **función**, un **clase** o alguna otra cosa.  Además, cada nombre debe declararse (directa o indirectamente) en cada archivo .cpp en el que se utiliza. Cuando se compila un programa, cada archivo .cpp se compila de forma independiente en una unidad de compilación. El compilador no tiene conocimiento de los nombres se declaran en otras unidades de compilación. Esto significa que si se define una clase o función o variable global, debe proporcionar una declaración de ese elemento en cada archivo .cpp adicionales que lo utilice. Cada declaración de ese elemento debe ser idéntico en todos los archivos. Una incoherencia ligera provocará errores o un comportamiento no deseado, cuando el vinculador intenta combinar todas las unidades de compilación en un único programa.

Para minimizar la posibilidad de errores, C++ adoptó la convención de usar *archivos de encabezado* para que contenga las declaraciones. Realizan las declaraciones en un archivo de encabezado, utilice el #include (directiva) en cada archivo .cpp u otro archivo de encabezado requiere esa declaración. El #include directiva inserta una copia del archivo de encabezado directamente en el archivo .cpp antes de la compilación. 

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una forma común para declarar una clase y, a continuación, utilizarlo en otro archivo de origen. Comenzaremos con el archivo de encabezado, **my_class.h**. Contiene una definición de clase, pero tenga en cuenta que la definición está incompleta; la función miembro `do_something` no está definido:

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

A continuación, cree un archivo de implementación (normalmente con una .cpp o extensión similar). Comenzaremos llame el archivo my_class.cpp y proporcionar una definición de la declaración del miembro. Agregamos una `#include` la directiva de archivo "my_class.h" para disponer de la declaración de my_class insertada en este momento en el .cpp y se incluyen  **\<iostream >** para incorporar los cambios en la declaración de `std::cout`. Tenga en cuenta que se usan comillas para los archivos de encabezado en el mismo directorio que el archivo de origen, y se utilizan corchetes angulares para encabezados de la biblioteca estándar. Además, varios encabezados de la biblioteca estándar no tiene .h o cualquier otra extensión de archivo.

En el archivo de implementación, podemos utilizar opcionalmente un **con** instrucción para evitar tener que calificar cada mención de "my_class" o "cout" con "N::" o "std::".  No incluya **con** las instrucciones en los archivos de encabezado.

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

Ahora podemos usar `my_class` en otro archivo. cpp. Se #include el archivo de encabezado para que el compilador extrae la declaración. Todas las necesidades de compilador saber es que my_class es una clase que tiene una función miembro público llama `do_something()`.

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

Después de que el compilador finalice la compilación de cada archivo .cpp en los archivos .obj, pasa los archivos obj al vinculador. Cuando el vinculador combina los archivos de objeto encuentra exactamente una definición para my_class; se encuentra en el archivo .obj que se genera para my_class.cpp y la compilación se realiza correctamente.

## <a name="include-guards"></a>Protecciones de inclusión

Normalmente, archivos de encabezado tienen un *#include guard* o un **una vez #pragma** directiva para asegurarse de que no se insertan varias veces en un archivo .cpp único. 

my_class.h
#<a name="ifndef-myclassh--include-guard"></a>IFNDEF MY_CLASS_H / / #include guard
#<a name="define-myclassh"></a>definir MY_CLASS_H


espacio de nombres N {clase my_class {public: void do_something();};

}

#<a name="endif--myclassh-"></a>endif / * MY_CLASS_H * /

## <a name="what-to-put-in-a-header-file"></a>Qué incluir en un archivo de encabezado

Dado que varios archivos potencialmente puede incluir un archivo de encabezado, no puede contener definiciones que podrían generar varias definiciones del mismo nombre. Los siguientes no se permiten o se consideran una práctica muy incorrecta:

- definiciones de tipo integrado en el ámbito global o de espacio de nombres
- definiciones de función no alineada 
- definiciones de variables no es const
- definiciones de agregado
- espacios de nombres sin nombre
- Directivas using

El uso de la **con** directiva no necesariamente se producirá un error, pero puede causar un problema ya que lleva el espacio de nombres en el ámbito de cada archivo .cpp que directa o indirectamente incluya ese encabezado. 

## <a name="sample-header-file"></a>Archivo de encabezado de ejemplo

El ejemplo siguiente muestra los distintos tipos de declaraciones y definiciones que se permiten en un archivo de encabezado:

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

---
title: Archivos de encabezado (C++) | Microsoft Docs
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
ms.openlocfilehash: 746b0829be6f66203d22cae4072dded9f6be32d8
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939707"
---
# <a name="header-files-c"></a>Archivos de encabezado (C++)

Antes de que se pueden usar, se deben declarar los nombres de elementos de programa como variables, funciones, clases y así sucesivamente. Por ejemplo, no se puede escribir simplemente `x = 42` sin declararla primero 'x'. 

```cpp
int x; // declaration
x = 42; // use x
```

 La declaración indica al compilador si es un **int**, un **doble**, un **función**, un **clase** o alguna otra cosa.  Además, cada nombre se debe declarar (directa o indirectamente) en cada archivo .cpp en el que se utiliza. Cuando se compila un programa, cada archivo .cpp se compila por separado en una unidad de compilación. El compilador no tiene conocimiento de qué nombres se declaran en otras unidades de compilación. Esto significa que si define una clase o función o variable global, debe proporcionar una declaración de eso en cada archivo .cpp adicionales que lo utiliza. Cada declaración de eso debe ser idéntico en todos los archivos. Una incoherencia leve provocará errores, o un comportamiento imprevisto, cuando el vinculador intenta combinar todas las unidades de compilación en un único programa.

Para minimizar la posibilidad de errores, C++ adoptó la convención de usar *archivos de encabezado* para contener las declaraciones. Realice las declaraciones en un archivo de encabezado y luego usar el #include (directiva) en cada archivo .cpp o de otro archivo de encabezado requiere la declaración. El #include directivas inserciones una copia del archivo de encabezado directamente en el archivo .cpp antes de la compilación. 

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra una forma habitual declarar una clase y, a continuación, utilizarlo en otro archivo de origen. Comenzaremos con el archivo de encabezado, `my_class.h`. Contiene una definición de clase, pero tenga en cuenta que la definición es incompleta; la función miembro `do_something` no está definida:

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

A continuación, cree un archivo de implementación (normalmente con un .cpp o extensión similar). Comenzaremos llamar a la my_class.cpp de archivo y proporcione una definición para la declaración del miembro. Agregamos un `#include` la directiva de archivo "my_class.h" con el fin de tener la declaración my_class insertada en este momento en el cpp archivo y se incluyen `<iostream>` para extraer la declaración para `std::cout`. Tenga en cuenta que las comillas se usan para los archivos de encabezado en el mismo directorio que el archivo de origen y se utilizan corchetes angulares para encabezados de la biblioteca estándar. Además, muchos de los encabezados de biblioteca estándar no tiene .h o cualquier otra extensión de archivo.

En el archivo de implementación, podemos usar opcionalmente un **mediante** instrucción para evitar tener que calificar cada mención de "my_class" o "cout" con "N::" o "std::".  No incluya **mediante** instrucciones en los archivos de encabezado.

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

Ahora podemos usar `my_class` en otro archivo. cpp. Nos #include el archivo de encabezado para que el compilador se extrae en la declaración. Todas las necesidades del compilador saber es que my_class es una clase que tiene una función miembro público llama `do_something()`.

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

## <a name="include-guards"></a>Restricciones de inclusión

Normalmente, los archivos de encabezado tienen un *#include guard* o un **#pragma una vez** directiva para asegurarse de que no se insertan varias veces en un archivo .cpp único. 

my_class.h
#<a name="ifndef-myclassh--include-guard"></a>IFNDEF MY_CLASS_H / / #include guard
#<a name="define-myclassh"></a>definir MY_CLASS_H


espacio de nombres N {clase my_class {public: void do_something();};

}

#<a name="endif--myclassh-"></a>endif / * MY_CLASS_H * /

## <a name="what-to-put-in-a-header-file"></a>Qué incluir en un archivo de encabezado

Dado que un archivo de encabezado podría incluirse potencialmente por varios archivos, no puede contener definiciones que podrían generar varias definiciones del mismo nombre. Los siguientes no se permiten o se consideran muy mala práctica:

- definiciones de tipo integrado en el ámbito global o de espacio de nombres
- definiciones de funciones no insertadas 
- definiciones de variable no constante
- definiciones de agregado
- espacios de nombres sin nombre
- Directivas using

El uso de la **mediante** directiva no necesariamente se producirá un error, pero puede provocar un problema ya que aporta el espacio de nombres en el ámbito de cada archivo .cpp que directa o indirectamente incluya ese encabezado. 

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

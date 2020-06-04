---
title: Espacios de nombres (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++]
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 4957ec5a5face860d2e39861eddc8f7e5abe9370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367913"
---
# <a name="namespaces-c"></a>Espacios de nombres (C++)

Un espacio de nombres es una región declarativa que proporciona un ámbito a los identificadores (nombres de tipos, funciones, variables, etc.) de su interior. Los espacios de nombres se utilizan para organizar el código en grupos lógicos y para evitar conflictos de nombres que pueden producirse, especialmente cuando la base de código incluye varias bibliotecas. Todos los identificadores del ámbito del espacio de nombres son visibles entre sí sin calificación. Los identificadores fuera del espacio de nombres pueden tener acceso `std::vector<std::string> vec;`a los miembros mediante el nombre`using std::string`completo de cada identificador, por ejemplo, o bien mediante una [declaración](../cpp/using-declaration.md) using para un único identificador ( ), o una [directiva using](../cpp/namespaces-cpp.md#using_directives) para todos los identificadores del espacio de nombres (`using namespace std;`). El código de los archivos de encabezado debe utilizar siempre el nombre completo del espacio de nombres.

En el ejemplo siguiente se muestra una declaración de espacio de nombres y tres formas de que el código que está fuera del espacio de nombres obtenga acceso a sus miembros.

```cpp
namespace ContosoData
{
    class ObjectManager
    {
    public:
        void DoSomething() {}
    };
    void Func(ObjectManager) {}
}
```

Use el nombre completo:

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

Use una declaración using para poner un identificador en el ámbito:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Use una directiva using para poner todo el espacio de nombres en el ámbito:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a name="using-directives"></a><a id="using_directives"></a>utilizando directivas

La directiva **using** permite usar todos los nombres de un **espacio** de nombres sin el *nombre-espacio* de nombres como calificador explícito. Utilice una directiva using en un archivo de implementación (es decir, *.cpp) si utiliza varios identificadores diferentes en un espacio de nombres; si solo usa uno o dos identificadores, considere la posibilidad de una declaración using para incorporar solo esos identificadores en el ámbito y no todos los identificadores del espacio de nombres. Si una variable local tiene el mismo nombre que una variable de espacio de nombres, se oculta la variable de espacio de nombres. Es un error tener una variable de espacio de nombres con el mismo nombre que una variable global.

> [!NOTE]
> Una directiva using puede colocarse en la parte superior del archivo .cpp (en el ámbito del archivo), o dentro de una definición de clase o función.
>
> En general, evite colocar directivas using en un archivo de encabezado (*. h) porque cualquier archivo que incluya ese encabezado pondrá todo en el espacio de nombres en el ámbito, lo que puede ocasionar problemas de ocultación de nombres y colisión de nombres que son muy difíciles de depurar. Utilice siempre nombres completos en los archivos de encabezado. Si esos nombres acaban siendo demasiado largos, puede utilizar un alias de espacio de nombres para acortarlos. (Vea a continuación).

## <a name="declaring-namespaces-and-namespace-members"></a>Declarar espacios de nombres y miembros de espacio de nombres

Normalmente, los espacios de nombres se declaran en un archivo de encabezado. Si las implementaciones de sus funciones están en un archivo independiente, complete los nombres de función, como en este ejemplo.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Las implementaciones de función en contosodata.cpp deben usar el nombre completo, incluso si coloca una directiva **using** en la parte superior del archivo:

```cpp
#include "contosodata.h"
using namespace ContosoDataServer;

void ContosoDataServer::Foo() // use fully-qualified name here
{
   // no qualification needed for Bar()
   Bar();
}

int ContosoDataServer::Bar(){return 0;}
```

Se puede declarar un espacio de nombres en varios bloques de un solo archivo y en varios archivos. El compilador une las partes durante el preprocesamiento y el espacio de nombres resultante contiene todos los miembros declarados en todas las partes. Un ejemplo de esto es el espacio de nombres std, que se declara en cada uno de los archivos de encabezado de la biblioteca estándar.

Los miembros de un espacio de nombres con nombre pueden definirse fuera del espacio de nombres en el que se declaran por calificación explícita del nombre que se define. Sin embargo, la definición debe aparecer después del punto de la declaración de un espacio de nombres que incluye el espacio de nombres de la declaración. Por ejemplo:

```cpp
// defining_namespace_members.cpp
// C2039 expected
namespace V {
    void f();
}

void V::f() { }        // ok
void V::g() { }        // C2039, g() is not yet a member of V

namespace V {
    void g();
}
```

Este error puede producirse cuando los miembros del espacio de nombres se declaran en varios archivos de encabezado y estos encabezados no se han incluido en el orden correcto.

## <a name="the-global-namespace"></a>El espacio de nombres global

Si un identificador no se declara en un espacio de nombres explícito, forma parte del espacio de nombres global implícito. En general, intente evitar realizar declaraciones en el ámbito global siempre que sea posible, excepto para la [función principal](../c-language/main-function-and-program-execution.md)del punto de entrada , que se requiere que esté en el espacio de nombres global. Para calificar explícitamente un identificador global, utilice el operador de resolución de ámbito sin nombre, como en `::SomeFunction(x);`. Así, el identificador se diferenciará de cualquier elemento que tenga el mismo nombre en otro espacio de nombres, y también facilitará que otras personas entiendan el código.

## <a name="the-std-namespace"></a>El espacio de nombres std

Todos los tipos y funciones de `std` biblioteca estándar de `std`C++ se declaran en el espacio de nombres o espacios de nombres anidados dentro de .

## <a name="nested-namespaces"></a>Espacios de nombres anidados

Los espacios de nombres pueden estar anidados. Un espacio de nombres anidado ordinario tiene acceso no calificado a los miembros de sus elementos primarios, pero los miembros primarios no tienen acceso no calificado al espacio de nombres anidado (a menos que se declare como en línea), como se muestra en el ejemplo siguiente:

```cpp
namespace ContosoDataServer
{
    void Foo();

    namespace Details
    {
        int CountImpl;
        void Ban() { return Foo(); }
    }

    int Bar(){...};
    int Baz(int i) { return Details::CountImpl; }
}
```

Los espacios de nombres anidados normales pueden utilizarse para encapsular los detalles de implementación internos que no forman parte de la interfaz pública del espacio de nombres primario.

## <a name="inline-namespaces-c-11"></a>Espacios de nombres alineados (C++ 11)

A diferencia de un espacio de nombres anidado normal, los miembros de un espacio de nombres alineado se tratan como miembros del espacio de nombres primario. Esta característica permite la búsqueda dependiente de argumentos en funciones sobrecargadas para trabajar con funciones que tienen sobrecargas en un elemento primario y un espacio de nombres anidado alineado. También permite declarar una especialización en un espacio de nombres primario para una plantilla que se declara en el espacio de nombres alineado. En el ejemplo siguiente se muestra cómo el código externo enlaza de forma predeterminada con el espacio de nombres alineado:

```cpp
//Header.h
#include <string>

namespace Test
{
    namespace old_ns
    {
        std::string Func() { return std::string("Hello from old"); }
    }

    inline namespace new_ns
    {
        std::string Func() { return std::string("Hello from new"); }
    }
}

#include "header.h"
#include <string>
#include <iostream>

int main()
{
    using namespace Test;
    using namespace std;

    string s = Func();
    std::cout << s << std::endl; // "Hello from new"
    return 0;
}
```

El siguiente ejemplo muestra cómo se puede declarar una especialización en un elemento primario de una plantilla que se declara en un espacio de nombres alineado:

```cpp
namespace Parent
{
    inline namespace new_ns
    {
         template <typename T>
         struct C
         {
             T member;
         };
    }
     template<>
     class C<int> {};
}
```

Puede usar espacios de nombres alineados como mecanismo de control de versiones para administrar los cambios en la interfaz pública de una biblioteca. Por ejemplo, puede crear un espacio de nombres primario único y encapsular cada versión de la interfaz en su propio espacio de nombres anidado dentro del elemento primario. El espacio de nombres que contiene la versión más reciente o preferida se califica como alineado y, por tanto, se expone como si fuera un miembro directo del espacio de nombres primario. El código del cliente que invoca la clase Parent::Class se enlazará automáticamente al nuevo código. Los clientes que prefieren usar la versión anterior siguen teniendo acceso a ella mediante la ruta de acceso completa al espacio de nombres anidado que contiene ese código.

La palabra clave inline se debe aplicar a la primera declaración del espacio de nombres en una unidad de compilación.

El ejemplo siguiente muestra dos versiones de una interfaz, cada una en un espacio de nombres anidado. El espacio de nombres `v_20` tiene algunas modificaciones en la interfaz `v_10` y se marca como alineado. El código de cliente que utiliza la nueva biblioteca y llama a `Contoso::Funcs::Add` invocará la versión v_20. El código que intente llamar a `Contoso::Funcs::Divide` obtendrá ahora un error de tiempo de compilación. Si realmente necesita esa función, puede obtener acceso a la versión `v_10` llamando explícitamente a `Contoso::v_10::Funcs::Divide`.

```cpp
namespace Contoso
{
    namespace v_10
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            T Divide(T a, T b);
        };
    }

    inline namespace v_20
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            std::vector<double> Log(double);
            T Accumulate(std::vector<T> nums);
      };
    }
}
```

## <a name="namespace-aliases"></a><a id="namespace_aliases"></a>Alias de espacio de nombres

Los nombres de los espacios de nombres deben ser únicos, lo que significa que a menudo no pueden ser demasiado cortos. Si la longitud de un nombre hace que el código sea difícil de leer, o es tedioso escribir en un archivo de encabezado donde no se puede usar el uso de directivas, puede crear un alias de espacio de nombres que sirva como abreviatura para el nombre real. Por ejemplo:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>espacios de nombres anónimos o sin nombre

Puede crear un espacio de nombres explícito, pero sin asignarle un nombre:

```cpp
namespace
{
    int MyFunc(){}
}
```

Esto se denomina espacio de nombres anónimo o sin nombre y resulta útil cuando se desea que las declaraciones de variables sean invisibles para el código de otros archivos (es decir, darles vinculación interna) sin tener que crear un espacio de nombres con nombre. Todo el código del mismo archivo puede ver los identificadores en un espacio de nombres sin nombre, pero los identificadores, junto con el espacio de nombres, no son visibles fuera de ese archivo, o más concretamente fuera de la unidad de traducción.

## <a name="see-also"></a>Consulte también

[Declaraciones y definiciones](declarations-and-definitions-cpp.md)

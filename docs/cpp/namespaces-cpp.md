---
title: Espacios de nombres (C++) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- namespace_CPP
- using_CPP
dev_langs:
- C++
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a68a0a67748e79fe4379cb5f820cca0c845f392
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405488"
---
# <a name="namespaces-c"></a>Espacios de nombres (C++)
Un espacio de nombres es una región declarativa que proporciona un ámbito a los identificadores (nombres de tipos, funciones, variables, etc.) de su interior. Los espacios de nombres se utilizan para organizar el código en grupos lógicos y para evitar conflictos de nombres que pueden producirse, especialmente cuando la base de código incluye varias bibliotecas. Todos los identificadores del ámbito del espacio de nombres son visibles entre sí sin calificación. Identificadores fuera del espacio de nombres pueden tener acceso a los miembros con el nombre completo para cada identificador, por ejemplo `std::vector<std::string> vec;`, o bien mediante un [mediante declaración](../cpp/using-declaration.md) para un identificador único (`using std::string`), o un [#using](../cpp/namespaces-cpp.md#using_directives) para todos los identificadores del espacio de nombres (`using namespace std;`). El código de los archivos de encabezado debe utilizar siempre el nombre completo del espacio de nombres.  
  
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
  
## <a id="using_directives"></a> directivas using  
 El **mediante** directiva permite que todos los nombres de un **espacio de nombres** utilizar sin el *espacio de nombres* como calificador explícito. Utilizar una directiva en un archivo de implementación (es decir, *.cpp) si está utilizando varios identificadores diferentes en un espacio de nombres; Si simplemente usa uno o dos identificadores, a continuación, considere el uso de una declaración para poner solo esos identificadores en el ámbito y no todos los identificadores del espacio de nombres. Si una variable local tiene el mismo nombre que una variable de espacio de nombres, se oculta la variable de espacio de nombres. Es un error tener una variable de espacio de nombres con el mismo nombre que una variable global.  
  
> [!NOTE]
>  Una directiva using puede colocarse en la parte superior del archivo .cpp (en el ámbito del archivo), o dentro de una definición de clase o función.  
>   
>  En general, evite colocar directivas using en un archivo de encabezado (*. h) porque cualquier archivo que incluya ese encabezado pondrá todo en el espacio de nombres en el ámbito, lo que puede ocasionar problemas de ocultación de nombres y colisión de nombres que son muy difíciles de depurar. Utilice siempre nombres completos en los archivos de encabezado. Si esos nombres acaban siendo demasiado largos, puede utilizar un alias de espacio de nombres para acortarlos. (Vea a continuación).  
  
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
  
 Las implementaciones de funciones en contosodata.cpp deben utilizar el nombre completo, incluso si coloca un **mediante** la directiva en la parte superior del archivo:  
  
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
  
 Los miembros de un espacio de nombres pueden definirse fuera del espacio de nombres en el que se declaran por calificación explícita del nombre que se está definiendo. Sin embargo, la definición debe aparecer después del punto de la declaración de un espacio de nombres que incluye el espacio de nombres de la declaración. Por ejemplo:  
  
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
}  
```  
  
 Este error puede producirse cuando los miembros del espacio de nombres se declaran en varios archivos de encabezado y estos encabezados no se han incluido en el orden correcto.  
  
## <a name="the-global-namespace"></a>El espacio de nombres global  
 Si un identificador no se declara en un espacio de nombres explícito, forma parte del espacio de nombres global implícito. En general, intente evitar las declaraciones en el ámbito global cuando sea posible, excepto para el punto de entrada [función main](../c-language/main-function-and-program-execution.md), que es necesario para estar en el espacio de nombres global. Para calificar explícitamente un identificador global, utilice el operador de resolución de ámbito sin nombre, como en `::SomeFunction(x);`. Así, el identificador se diferenciará de cualquier elemento que tenga el mismo nombre en otro espacio de nombres, y también facilitará que otras personas entiendan el código.  
  
## <a name="the-std-namespace"></a>El espacio de nombres std  
 Todos los tipos de la biblioteca estándar de C++ y las funciones se declaran en el `std` espacio de nombres o espacios de nombres anidado dentro de `std`.  
  
## <a name="nested-namespaces"></a>Espacios de nombres anidados  
 Los espacios de nombres pueden estar anidados. Un espacio de nombres anidado normal tiene acceso incompleto a los miembros de su elemento primario, pero los miembros primarios no tienen acceso incompleto al espacio de nombres anidado (a menos que se declare como alineado), como se muestra en el ejemplo siguiente:  
  
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
  
## <a id="namespace_aliases"></a> Alias Namespace  
 Los nombres de los espacios de nombres deben ser únicos, lo que significa que a menudo no pueden ser demasiado cortos. Si la longitud de un nombre hace que el código sea difícil de leer, o resulta tedioso escribirlo en un archivo de encabezado donde no se pueden utilizar directivas using, puede hacer un alias del espacio de nombres que actúe como una abreviatura del nombre real. Por ejemplo:  
  
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
  
 Esto se conoce como un espacio de nombres sin nombre o anónimo y resulta útil cuando desea que las declaraciones de variable invisibles para el código en otros archivos (es decir, darles vinculación interna) sin tener que crear un espacio de nombres. Todo el código del mismo archivo puede ver los identificadores en un espacio de nombres sin nombre, pero los identificadores, junto con el espacio de nombres, no son visibles fuera de ese archivo, o más concretamente fuera de la unidad de traducción.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones y definiciones](declarations-and-definitions-cpp.md)
---
title: Procedimiento Exponer un contenedor STL/CLR desde un ensamblado
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
ms.openlocfilehash: 206a95cbaa808f54d7ae0e500b5a2bea272d974b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387336"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>Procedimiento Exponer un contenedor STL/CLR desde un ensamblado

Contenedores STL/CLR como `list` y `map` se implementan como clases ref de plantilla. Dado que se crean instancias de las plantillas de C++ en tiempo de compilación, dos clases de plantilla que tienen exactamente la misma firma pero están en distintos ensamblados son realmente diferentes tipos. Esto significa que no se puede usar las clases de plantilla entre límites de ensamblado.

Para que compartir entre ensamblados sea posible, los contenedores STL/CLR implementan la interfaz genérica <xref:System.Collections.Generic.ICollection%601>. Mediante el uso de esta interfaz genérica, todos los idiomas que admiten genéricos, incluidos C++, C# y Visual Basic, pueden tener acceso a los contenedores STL/CLR.

Este tema muestra cómo mostrar los elementos de varios contenedores STL/CLR escritos en un ensamblado de C++ llamado `StlClrClassLibrary`. Se muestran dos ensamblados para tener acceso a `StlClrClassLibrary`. El primer ensamblado está escrito en C++ y la segunda en C#.

Si ambos ensamblados están escritos en C++, puede acceder a la interfaz genérica de un contenedor mediante su `generic_container` typedef. Por ejemplo, si tiene un contenedor de tipo `cliext::vector<int>`, entonces su interfaz genérica es: `cliext::vector<int>::generic_container`. De forma similar, puede obtener un iterador a través de la interfaz genérica mediante la `generic_iterator` typedef, como en: `cliext::vector<int>::generic_iterator`.

Dado que estas definiciones de tipos se declaran en los archivos de encabezado de C++, los ensamblados escritos en otros lenguajes no pueden utilizarlos. Por lo tanto, para tener acceso a la interfaz genérica para `cliext::vector<int>` en C# o cualquier otro lenguaje. NET, use `System.Collections.Generic.ICollection<int>`. Para recorrer en iteración esta colección, use un `foreach` bucle.

La tabla siguiente muestra la interfaz genérica que implementa cada contenedor STL/CLR:

|Contenedor STL/CLR|Interfaz genérica|
|------------------------|-----------------------|
|`deque<T>`|`ICollection<T>`|
|`hash_map<K, V>`|`IDictionary<K, V>`|
|`hash_multimap<K, V>`|`IDictionary<K, V>`|
|`hash_multiset<T>`|`ICollection<T>`|
|`hash_set<T>`|`ICollection<T>`|
|`list<T>`|`ICollection<T>`|
|`map<K, V>`|`IDictionary<K, V>`|
|`multimap<K, V>`|`IDictionary<K, V>`|
|`multiset<T>`|`ICollection<T>`|
|`set<T>`|`ICollection<T>`|
|`vector<T>`|`ICollection<T>`|

> [!NOTE]
> Dado que el `queue`, `priority_queue`, y `stack` contenedores no admiten iteradores, que no implementan las interfaces genéricas y no pueden ser entre ensamblados a los que accede.

## <a name="example-1"></a>Ejemplo 1

### <a name="description"></a>Descripción

En este ejemplo, se declara una clase de C++ que contiene los datos de miembros privados de STL/CLR. A continuación, declaramos métodos públicos para conceder acceso a las colecciones de la clase privadas. Hacemos lo de dos maneras diferentes, uno para los clientes C++ y otro para otros clientes. NET.

### <a name="code"></a>Código

```cpp
// StlClrClassLibrary.h
#pragma once

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/stack>
#include <cliext/vector>

using namespace System;
using namespace System::Collections::Generic;
using namespace cliext;

namespace StlClrClassLibrary {

    public ref class StlClrClass
    {
    public:
        StlClrClass();

        // These methods can be called by a C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        deque<wchar_t>::generic_container ^GetDequeCpp();
        list<float>::generic_container ^GetListCpp();
        map<int, String ^>::generic_container ^GetMapCpp();
        set<double>::generic_container ^GetSetCpp();
        vector<int>::generic_container ^GetVectorCpp();

        // These methods can be called by a non-C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        ICollection<wchar_t> ^GetDequeCs();
        ICollection<float> ^GetListCs();
        IDictionary<int, String ^> ^GetMapCs();
        ICollection<double> ^GetSetCs();
        ICollection<int> ^GetVectorCs();

    private:
        deque<wchar_t> ^aDeque;
        list<float> ^aList;
        map<int, String ^> ^aMap;
        set<double> ^aSet;
        vector<int> ^aVector;
    };
}
```

## <a name="example-2"></a>Ejemplo 2

### <a name="description"></a>Descripción

En este ejemplo, implementamos la clase declarada en el ejemplo 1. Para que los clientes usar esta biblioteca de clases, usamos la herramienta de manifiesto **mt.exe** para incrustar el archivo de manifiesto en el archivo DLL. Para obtener más información, vea los comentarios del código.

Para obtener más información sobre la herramienta de manifiesto y los ensamblados en paralelo, vea [creación de aplicaciones aisladas de C/C ++ y ensamblados en paralelo](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

### <a name="code"></a>Código

```cpp
// StlClrClassLibrary.cpp
// compile with: /clr /LD /link /manifest
// post-build command: (attrib -r StlClrClassLibrary.dll & mt /manifest StlClrClassLibrary.dll.manifest /outputresource:StlClrClassLibrary.dll;#2 & attrib +r StlClrClassLibrary.dll)

#include "StlClrClassLibrary.h"

namespace StlClrClassLibrary
{
    StlClrClass::StlClrClass()
    {
        aDeque = gcnew deque<wchar_t>();
        aDeque->push_back(L'a');
        aDeque->push_back(L'b');

        aList = gcnew list<float>();
        aList->push_back(3.14159f);
        aList->push_back(2.71828f);

        aMap = gcnew map<int, String ^>();
        aMap[0] = "Hello";
        aMap[1] = "World";

        aSet = gcnew set<double>();
        aSet->insert(3.14159);
        aSet->insert(2.71828);

        aVector = gcnew vector<int>();
        aVector->push_back(10);
        aVector->push_back(20);
    }

    deque<wchar_t>::generic_container ^StlClrClass::GetDequeCpp()
    {
        return aDeque;
    }

    list<float>::generic_container ^StlClrClass::GetListCpp()
    {
        return aList;
    }

    map<int, String ^>::generic_container ^StlClrClass::GetMapCpp()
    {
        return aMap;
    }

    set<double>::generic_container ^StlClrClass::GetSetCpp()
    {
        return aSet;
    }

    vector<int>::generic_container ^StlClrClass::GetVectorCpp()
    {
        return aVector;
    }

    ICollection<wchar_t> ^StlClrClass::GetDequeCs()
    {
        return aDeque;
    }

    ICollection<float> ^StlClrClass::GetListCs()
    {
        return aList;
    }

    IDictionary<int, String ^> ^StlClrClass::GetMapCs()
    {
        return aMap;
    }

    ICollection<double> ^StlClrClass::GetSetCs()
    {
        return aSet;
    }

    ICollection<int> ^StlClrClass::GetVectorCs()
    {
        return aVector;
    }
}
```

## <a name="example-3"></a>Ejemplo 3

### <a name="description"></a>Descripción

En este ejemplo, crearemos a un cliente de C++ que utiliza la biblioteca de clases creada en los ejemplos 1 y 2. Este cliente utiliza el `generic_container` definiciones de tipos de los contenedores STL/CLR para recorrer en iteración los contenedores y mostrar su contenido.

### <a name="code"></a>Código

```cpp
// CppConsoleApp.cpp
// compile with: /clr /FUStlClrClassLibrary.dll

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/vector>

using namespace System;
using namespace StlClrClassLibrary;
using namespace cliext;

int main(array<System::String ^> ^args)
{
    StlClrClass theClass;

    Console::WriteLine("cliext::deque contents:");
    deque<wchar_t>::generic_container ^aDeque = theClass.GetDequeCpp();
    for each (wchar_t wc in aDeque)
    {
        Console::WriteLine(wc);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::list contents:");
    list<float>::generic_container ^aList = theClass.GetListCpp();
    for each (float f in aList)
    {
        Console::WriteLine(f);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::map contents:");
    map<int, String ^>::generic_container ^aMap = theClass.GetMapCpp();
    for each (map<int, String ^>::value_type rp in aMap)
    {
        Console::WriteLine("{0} {1}", rp->first, rp->second);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::set contents:");
    set<double>::generic_container ^aSet = theClass.GetSetCpp();
    for each (double d in aSet)
    {
        Console::WriteLine(d);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::vector contents:");
    vector<int>::generic_container ^aVector = theClass.GetVectorCpp();
    for each (int i in aVector)
    {
        Console::WriteLine(i);
    }
    Console::WriteLine();

    return 0;
}
```

### <a name="output"></a>Salida

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="example-4"></a>Ejemplo 4

### <a name="description"></a>Descripción

En este ejemplo, crearemos a un cliente de C# que utiliza la biblioteca de clases creada en los ejemplos 1 y 2. Este cliente utiliza el <xref:System.Collections.Generic.ICollection%601> métodos de los contenedores STL/CLR para recorrer en iteración los contenedores y mostrar su contenido.

### <a name="code"></a>Código

```csharp
// CsConsoleApp.cs
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll

using System;
using System.Collections.Generic;
using StlClrClassLibrary;
using cliext;

namespace CsConsoleApp
{
    class Program
    {
        static int Main(string[] args)
        {
            StlClrClass theClass = new StlClrClass();

            Console.WriteLine("cliext::deque contents:");
            ICollection<char> iCollChar = theClass.GetDequeCs();
            foreach (char c in iCollChar)
            {
                Console.WriteLine(c);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::list contents:");
            ICollection<float> iCollFloat = theClass.GetListCs();
            foreach (float f in iCollFloat)
            {
                Console.WriteLine(f);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::map contents:");
            IDictionary<int, string> iDict = theClass.GetMapCs();
            foreach (KeyValuePair<int, string> kvp in iDict)
            {
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::set contents:");
            ICollection<double> iCollDouble = theClass.GetSetCs();
            foreach (double d in iCollDouble)
            {
                Console.WriteLine(d);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::vector contents:");
            ICollection<int> iCollInt = theClass.GetVectorCs();
            foreach (int i in iCollInt)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            return 0;
        }
    }
}
```

### <a name="output"></a>Salida

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="see-also"></a>Vea también

[Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)

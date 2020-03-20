---
title: 'Cómo: Convertir una colección .NET en un contenedor STL/CLR'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 156b4162f742915939ebdfaec6a84d77afaad8cd
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545052"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Cómo: Convertir una colección .NET en un contenedor STL/CLR

En este tema se muestra cómo convertir colecciones de .NET en sus contenedores de STL/CLR equivalentes. Como ejemplo, se muestra cómo convertir un <xref:System.Collections.Generic.List%601> .NET en un [Vector](../dotnet/vector-stl-clr.md) de STL/CLR y cómo convertir un <xref:System.Collections.Generic.Dictionary%602> .net en una [asignación](../dotnet/map-stl-clr.md)de STL/CLR, pero el procedimiento es similar para todas las colecciones y contenedores.

### <a name="to-create-a-container-from-a-collection"></a>Para crear un contenedor a partir de una colección

1. Para convertir una colección completa, cree un contenedor de STL/CLR y pase la colección al constructor.

   En el primer ejemplo se muestra este procedimiento.

O

1. Cree un contenedor de STL/CLR genérico mediante la creación de un objeto de [collection_adapter](../dotnet/collection-adapter-stl-clr.md) . Esta clase de plantilla toma una interfaz de colección .NET como argumento. Para comprobar qué interfaces se admiten, vea [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Copie el contenido de la colección .NET en el contenedor. Esto puede hacerse mediante el uso de un [algoritmo](../dotnet/algorithm-stl-clr.md)de STL/CLR, o bien recorriendo en iteración la colección .net e insertando una copia de cada elemento en el contenedor de STL/CLR.

   En el segundo ejemplo se muestra este procedimiento.

## <a name="example"></a>Ejemplo

En este ejemplo, se crea un <xref:System.Collections.Generic.List%601> genérico y se le agregan 5 elementos. A continuación, creamos un `vector` mediante el constructor que toma un <xref:System.Collections.Generic.IEnumerable%601> como un argumento.

```cpp
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>Ejemplo

En este ejemplo, se crea un <xref:System.Collections.Generic.Dictionary%602> genérico y se le agregan 5 elementos. A continuación, creamos un `collection_adapter` para encapsular el <xref:System.Collections.Generic.Dictionary%602> como un contenedor STL/CLR simple. Por último, se crea una `map` y se copia el contenido del <xref:System.Collections.Generic.Dictionary%602> en el `map` recorriendo en iteración el `collection_adapter`. Durante este proceso, se crea un nuevo par mediante el uso de la función `make_pair` e inserta el par nuevo directamente en el `map`.

```cpp
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Consulte también

[Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Cómo: Convertir un contenedor STL/CLR en una colección .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)

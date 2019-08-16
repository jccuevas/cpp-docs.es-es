---
title: Procedimiento Convertir una colección .NET en un contenedor STL/CLR
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 836623f6d539b7b28765763a3dc36d477f8c1499
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387557"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Procedimiento Convertir una colección .NET en un contenedor STL/CLR

En este tema se muestra cómo convertir las colecciones de .NET a sus contenedores STL/CLR equivalente. Como ejemplo se muestra cómo convertir un .NET <xref:System.Collections.Generic.List%601> a STL/CLR [vector](../dotnet/vector-stl-clr.md) y cómo convertir un .NET <xref:System.Collections.Generic.Dictionary%602> a STL/CLR [mapa](../dotnet/map-stl-clr.md), pero el procedimiento es similar para todas las colecciones y contenedores .

### <a name="to-create-a-container-from-a-collection"></a>Para crear un contenedor de una colección

1. Para convertir una colección completa, cree un contenedor STL/CLR y pasar al constructor de la colección.

   El primer ejemplo muestra este procedimiento.

O BIEN

1. Crear un contenedor STL/CLR genérico mediante la creación de un [collection_adapter](../dotnet/collection-adapter-stl-clr.md) objeto. Esta clase de plantilla toma una interfaz de colección de .NET como un argumento. Para comprobar qué interfaces son compatibles, consulte [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Copie el contenido de la colección de .NET en el contenedor. Esto puede hacerse mediante el uso de STL/CLR [algoritmo](../dotnet/algorithm-stl-clr.md), o bien, recorrer en iteración la colección de .NET y la inserción de una copia de cada elemento en el contenedor STL/CLR.

   El segundo ejemplo muestra este procedimiento.

## <a name="example"></a>Ejemplo

En este ejemplo, vamos a crear un tipo genérico <xref:System.Collections.Generic.List%601> y agregarle 5 elementos. A continuación, creamos un `vector` utilizando el constructor que toma un <xref:System.Collections.Generic.IEnumerable%601> como argumento.

```
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

En este ejemplo, vamos a crear un tipo genérico <xref:System.Collections.Generic.Dictionary%602> y agregarle 5 elementos. A continuación, creamos un `collection_adapter` para ajustar el <xref:System.Collections.Generic.Dictionary%602> como un simple contenedor STL/CLR. Por último, crearemos un `map` y copie el contenido de la <xref:System.Collections.Generic.Dictionary%602> a la `map` repitiendo el `collection_adapter`. Durante este proceso, creamos un nuevo par mediante el uso de la `make_pair` función e insertar el nuevo par directamente en el `map`.

```
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

## <a name="see-also"></a>Vea también

[Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Cómo: Convertir un contenedor STL/CLR en una colección .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)

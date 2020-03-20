---
title: 'Cómo: Convertir un contenedor STL/CLR en una colección .NET'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: f7539b10ca6c503aede61d19de3d14fb9dcee8be
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545310"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Cómo: Convertir un contenedor STL/CLR en una colección .NET

En este tema se muestra cómo convertir contenedores de STL/CLR en sus colecciones de .NET equivalentes. Por ejemplo, se muestra cómo convertir un [Vector](../dotnet/vector-stl-clr.md) de STL/CLR en un <xref:System.Collections.Generic.ICollection%601> de .net y cómo convertir una [asignación](../dotnet/map-stl-clr.md) de STL/CLR a un <xref:System.Collections.Generic.IDictionary%602>de .net, pero el procedimiento es similar para todas las colecciones y contenedores.

### <a name="to-create-a-collection-from-a-container"></a>Para crear una colección a partir de un contenedor

1. Utilice uno de los métodos siguientes:

   - Para convertir parte de un contenedor, llame a la función [make_collection](../dotnet/make-collection-stl-clr.md) y pase los iteradores Begin y end del contenedor STL/CLR que se van a copiar en la colección .net. Esta función de plantilla toma un iterador de STL/CLR como argumento de plantilla. En el primer ejemplo se muestra este método.

   - Para convertir un contenedor completo, convierta el contenedor en una interfaz de colección .NET adecuada o en una colección de interfaces. En el segundo ejemplo se muestra este método.

## <a name="example"></a>Ejemplo

En este ejemplo, se crea un `vector` de STL/CLR y se le agregan 5 elementos. A continuación, creamos una colección .NET llamando a la función `make_collection`. Por último, se muestra el contenido de la colección recién creada.

```cpp
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

## <a name="example"></a>Ejemplo

En este ejemplo, se crea un `map` de STL/CLR y se le agregan 5 elementos. A continuación, creamos un <xref:System.Collections.Generic.IDictionary%602> .NET y le asignamos el `map` directamente. Por último, se muestra el contenido de la colección recién creada.

```cpp
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Consulte también

[Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[Cómo: Convertir una colección .NET en un contenedor STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)

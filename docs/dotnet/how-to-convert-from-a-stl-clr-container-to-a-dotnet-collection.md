---
title: Procedimiento Convertir un contenedor STL/CLR en una colección .NET
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: cf67e362751dd164916cc94cd644d55110d88a5f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751588"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Filtrar Convertir un contenedor STL/CLR en una colección .NET

En este tema se muestra cómo convertir los contenedores STL/CLR en sus colecciones de .NET equivalente. Por ejemplo, se muestra cómo convertir un STL/CLR [vector](../dotnet/vector-stl-clr.md) para .NET <xref:System.Collections.Generic.ICollection%601> y cómo convertir un STL/CLR [mapa](../dotnet/map-stl-clr.md) para .NET <xref:System.Collections.Generic.IDictionary%602>, pero el procedimiento es similar para todas las colecciones y contenedores.

### <a name="to-create-a-collection-from-a-container"></a>Para crear una colección de un contenedor

1. Use uno de los métodos siguientes:

   - Para convertir la parte de un contenedor, llame el [make_collection](../dotnet/make-collection-stl-clr.md) función y pasar el iterador inicial y el iterador de final del contenedor STL/CLR que se copiará en la colección de .NET. Esta función de plantilla toma un iterador STL/CLR como un argumento de plantilla. El primer ejemplo muestra este método.

   - Para convertir todo un contenedor, puede convertir el contenedor para una interfaz de colección adecuada de .NET o una colección de la interfaz. El segundo ejemplo muestra este método.

## <a name="example"></a>Ejemplo

En este ejemplo, creamos un STL/CLR `vector` y agregarle 5 elementos. A continuación, creamos una colección de .NET mediante una llamada a la `make_collection` función. Por último, se muestra el contenido de la colección recién creado.

```
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

En este ejemplo, creamos un STL/CLR `map` y agregarle 5 elementos. A continuación, creamos un .NET <xref:System.Collections.Generic.IDictionary%602> y asignar la `map` directamente a él. Por último, se muestra el contenido de la colección recién creado.

```
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

## <a name="see-also"></a>Vea también

[Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[Cómo: Convertir una colección .NET en un contenedor STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)

---
title: 'Cómo: convertir un contenedor STL/CLR en una colección .NET | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7fb4938121d1d2beed3133bee6013e17d37f1402
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Cómo: Convertir un contenedor STL/CLR en una colección .NET
Este tema muestra cómo convertir los contenedores STL/CLR en sus colecciones de .NET equivalentes. Por ejemplo, se muestra cómo convertir un STL/CLR [vector](../dotnet/vector-stl-clr.md) para .NET <xref:System.Collections.Generic.ICollection%601> y cómo convertir un STL/CLR [mapa](../dotnet/map-stl-clr.md) para .NET <xref:System.Collections.Generic.IDictionary%602>, pero el procedimiento es similar para todas las colecciones y contenedores.  
  
### <a name="to-create-a-collection-from-a-container"></a>Para crear una colección de un contenedor  
  
1.  Use uno de los métodos siguientes:  
  
    -   Para convertir la parte de un contenedor, llame a la [make_collection](../dotnet/make-collection-stl-clr.md) función y pase el iterador de inicio y el iterador de final del contenedor STL/CLR que se copiará en la colección de .NET. Esta función de plantilla tiene un iterador STL/CLR como un argumento de plantilla. El primer ejemplo muestra este método.  
  
    -   Para convertir todo un contenedor, convierte el contenedor para una interfaz de colección adecuada de .NET o una colección de interfaz. El segundo ejemplo muestra este método.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, crearemos un STL/CLR `vector` y agregarle 5 elementos. A continuación, creamos una colección .NET mediante una llamada a la `make_collection` (función). Por último, se muestra el contenido de la colección recién creada.  
  
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
 En este ejemplo, crearemos un STL/CLR `map` y agregarle 5 elementos. A continuación, creamos un .NET <xref:System.Collections.Generic.IDictionary%602> y asignar el `map` directamente a él. Por último, se muestra el contenido de la colección recién creada.  
  
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
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)   
 [Cómo: convertir una colección .NET en un contenedor STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)   
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
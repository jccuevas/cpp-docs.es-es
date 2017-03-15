---
title: "C&#243;mo: Convertir un contenedor STL/CLR en una colecci&#243;n .NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores STL/CLR [STL/CLR]"
  - "STL/CLR, convertir a colecciones .NET"
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Convertir un contenedor STL/CLR en una colecci&#243;n .NET
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo convertir los contenedores de STL\/CLR a las colecciones equivalentes de .NET.  Como ejemplo, mostramos cómo convertir un STL\/CLR [vector](../dotnet/vector-stl-clr.md) a .NET <xref:System.Collections.Generic.ICollection%601> y cómo convertir un STL\/CLR [Mapa](../dotnet/map-stl-clr.md) a .NET <xref:System.Collections.Generic.IDictionary%602>, pero el procedimiento es similar para todas las colecciones y contenedores.  
  
### Para crear una colección de un contenedor  
  
1.  Use uno de los métodos siguientes:  
  
    -   Para convertir la parte de un contenedor, llamar a la función de [make\_collection](../dotnet/make-collection-stl-clr.md) , y pasar el iterador de inicio y el iterador de final del contenedor de STL\/CLR se copie en la colección de .NET.  Esta función de plantilla toma un iterador de STL\/CLR como argumento de plantilla.  El primer ejemplo se muestra este método.  
  
    -   Para convertir un contenedor completo, convierta el contenedor a una colección adecuada de la interfaz de intercalación o interfaz.NET.  El segundo ejemplo se muestra este método.  
  
## Ejemplo  
 En este ejemplo, creamos un STL\/CLR `vector` y agregamos 5 elementos a.  A continuación, creamos una colección .NET llamando a la función de `make_collection` .  Finalmente, se muestra el contenido de la colección recién creada.  
  
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
  
  **El contenido de System::Collections::Generic::ICollection son:**  
**3**  
**5**  
**7**   
## Ejemplo  
 En este ejemplo, creamos un STL\/CLR `map` y agregamos 5 elementos a.  A continuación, creamos .NET <xref:System.Collections.Generic.IDictionary%602> y asignar `map` directamente al.  Finalmente, se muestra el contenido de la colección recién creada.  
  
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
  
  **El contenido de IDictionary son:**  
**Clave: valor 0.00: 0**  
**Clave: valor 13.00: 13**  
**Clave: valor 22.00: 22**  
**Clave: valor 42.00: 42**  
**Clave: valor 74.00: 74**   
## Vea también  
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)   
 [Cómo: Convertir una colección .NET en un contenedor STL\/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)   
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)
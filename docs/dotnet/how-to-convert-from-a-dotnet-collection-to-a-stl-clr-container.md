---
title: "C&#243;mo: Convertir una colecci&#243;n .NET en un contenedor STL/CLR | Microsoft Docs"
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
  - "STL/CLR, convertir de colecciones .NET"
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Convertir una colecci&#243;n .NET en un contenedor STL/CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo convertir colecciones.NET a sus contenedores de equivalente STL\/CLR.  Como ejemplo muestran cómo convertir .NET <xref:System.Collections.Generic.List%601> un STL\/CLR [vector](../dotnet/vector-stl-clr.md) y cómo convertir .NET <xref:System.Collections.Generic.Dictionary%602> un STL\/CLR [Mapa](../dotnet/map-stl-clr.md), pero el procedimiento es similar para todas las colecciones y contenedores.  
  
### Para crear un contenedor de una colección  
  
1.  Para convertir una colección completa, crear un contenedor de STL\/CLR y pase la colección al constructor.  
  
     El primer ejemplo se muestra este procedimiento.  
  
 O bien  
  
1.  Cree un contenedor genérico de STL\/CLR creando un objeto de [collection\_adapter](../dotnet/collection-adapter-stl-clr.md) .  Esta clase de plantilla toma una interfaz de intercalación de .NET como argumento.  Para comprobar si se admiten las interfaces, vea [collection\_adapter](../dotnet/collection-adapter-stl-clr.md).  
  
2.  Copie el contenido de la colección.NET al contenedor.  Esto se puede hacer utilizando un STL\/CLR [algoritmo](../dotnet/algorithm-stl-clr.md), o itera en la colección de .NET y insertando una copia de cada elemento en el contenedor de STL\/CLR.  
  
     El segundo ejemplo se muestra este procedimiento.  
  
## Ejemplo  
 En este ejemplo, creamos <xref:System.Collections.Generic.List%601> genérico y agregamos 5 elementos a.  A continuación, creamos `vector` mediante el constructor que toma <xref:System.Collections.Generic.IEnumerable%601> como argumento.  
  
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
  
  **El contenido de cliext::vector son:**  
**2**  
**3**  
**5**  
**7**  
**11**   
## Ejemplo  
 En este ejemplo, creamos <xref:System.Collections.Generic.Dictionary%602> genérico y agregamos 5 elementos a.  A continuación, creamos `collection_adapter` para ajustar <xref:System.Collections.Generic.Dictionary%602> como contenedor simple de STL\/CLR.  Finalmente, creamos `map` y copiamos el contenido de <xref:System.Collections.Generic.Dictionary%602> a `map` itera en `collection_adapter`.  Durante este proceso, crea un nuevo par mediante la función de `make_pair` , y insertamos nuevos pares directamente en `map`.  
  
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
  
  **El contenido de cliext::map son:**  
**Clave: valor 0.00: 0**  
**Clave: valor 13.00: 13**  
**Clave: valor 22.00: 22**  
**Clave: valor 42.00: 42**  
**Clave: valor 74.00: 74**   
## Vea también  
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)   
 [adapter](../dotnet/adapter-stl-clr.md)   
 [Cómo: Convertir un contenedor STL\/CLR en una colección .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
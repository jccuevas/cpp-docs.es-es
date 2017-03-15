---
title: "collection_adapter (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::collection_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collection_adapter (clase) [STL/CLR]"
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# collection_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene una colección de .NET para su uso como contenedor de STL\/CLR.  `collection_adapter` es una clase de plantilla que describe un objeto contenedor simple de STL\/CLR.  Contiene una interfaz de \(BCL\) de la biblioteca de clases base, y devuelve un par de iterador que utilizará para manipular la secuencia controlada.  
  
## Sintaxis  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### Parámetros  
 Coll  
 El tipo de colección ajustada.  
  
## Especializaciones  
  
|Especialización|Descripción|  
|---------------------|-----------------|  
|IEnumerable|Secuencias a través de los elementos.|  
|ICollection|Mantiene un grupo de elementos.|  
|IList|Mantiene un grupo ordenado de elementos.|  
|IDictionary|Mantiene un conjunto {clave, valor} de pares.|  
|IEnumerableValue\<\>|Secuencias mediante elementos escritos.|  
|ICollectionValue\<\>|Mantiene un grupo de elementos escritos.|  
|IListValue\<\>|Mantiene un grupo ordenado de elementos escritos.|  
|IDictionaryValue\<\>|Mantiene un conjunto {clave, valor} de pares escritos.|  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[collection\_adapter::difference\_type](../dotnet/collection-adapter-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[collection\_adapter::iterator](../dotnet/collection-adapter-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[collection\_adapter::key\_type](../dotnet/collection-adapter-key-type-stl-clr.md)|El tipo de una clave de diccionario.|  
|[collection\_adapter::mapped\_type](../dotnet/collection-adapter-mapped-type-stl-clr.md)|El tipo de un valor del diccionario.|  
|[collection\_adapter::reference](../dotnet/collection-adapter-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[collection\_adapter::size\_type](../dotnet/collection-adapter-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[collection\_adapter::value\_type](../dotnet/collection-adapter-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[collection\_adapter::base](../dotnet/collection-adapter-base-stl-clr.md)|Elija la interfaz ajustada de BCL.|  
|[collection\_adapter::begin](../dotnet/collection-adapter-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[collection\_adapter::collection\_adapter](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|Construye un objeto de adaptador.|  
|[collection\_adapter::end](../dotnet/collection-adapter-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[collection\_adapter::size](../dotnet/collection-adapter-size-stl-clr.md)|Cuenta el número de elementos.|  
|[collection\_adapter::swap](../dotnet/collection-adapter-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[collection\_adapter::operator\=](../dotnet/collection-adapter-operator-assign-stl-clr.md)|Reemplaza el identificador almacenado de BCL.|  
  
## Comentarios  
 Utiliza esta clase de plantilla para manipular un contenedor de BCL como contenedor de STL\/CLR.  `collection_adapter` almacena un identificador a una interfaz de BCL, que a su vez controla una secuencia de elementos.  Un objeto `X` de `collection_adapter` devuelve un par de iteradores `X.begin()` y `X.end()` de entrada que usa para visitar los elementos, en orden.  Algunas de las especializaciones también permiten escribir `X.size()` para determinar la longitud de la secuencia controlada.  
  
## Requisitos  
 cliext \<\/adaptador de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)   
 [make\_collection](../dotnet/make-collection-stl-clr.md)
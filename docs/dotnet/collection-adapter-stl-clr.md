---
title: collection_adapter (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::collection_adapter
dev_langs:
- C++
helpviewer_keywords:
- collection_adapter class [STL/CLR]
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a1a03dd6ecc52cd3921428e681fe5affa11d275
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="collectionadapter-stlclr"></a>collection_adapter (STL/CLR)
Encapsula una colección de .NET para su uso como un contenedor STL/CLR. A `collection_adapter` es una clase de plantilla que describe un objeto de contenedor STL/CLR simple. Ajusta una interfaz de biblioteca de clases Base (BCL) y devuelve un par de iteradores que se utiliza para manipular la secuencia controlada.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 Coll  
 El tipo de la colección ajustada.  
  
## <a name="specializations"></a>Especializaciones  
  
|Especialización|Descripción|  
|--------------------|-----------------|  
|IEnumerable|Secuencias a través de los elementos.|  
|ICollection|Mantiene un grupo de elementos.|  
|IList|Mantiene un grupo ordenado de elementos.|  
|IDictionary|Mantener un conjunto de {clave, valor} pares.|  
|IEnumerable\<valor >|Secuencias a través de los elementos con tipo.|  
|ICollection\<valor >|Mantiene un grupo de elementos con tipo.|  
|IList\<valor >|Mantiene un grupo ordenado de elementos con tipo.|  
|IDictionary\<valor >|Mantiene un conjunto de tipo {clave, valor} pares.|  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](../dotnet/collection-adapter-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[collection_adapter::iterator (STL/CLR)](../dotnet/collection-adapter-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[collection_adapter::key_type (STL/CLR)](../dotnet/collection-adapter-key-type-stl-clr.md)|El tipo de una clave de diccionario.|  
|[collection_adapter::mapped_type (STL/CLR)](../dotnet/collection-adapter-mapped-type-stl-clr.md)|El tipo de un valor del diccionario.|  
|[collection_adapter::reference (STL/CLR)](../dotnet/collection-adapter-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[collection_adapter::size_type (STL/CLR)](../dotnet/collection-adapter-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[collection_adapter::value_type (STL/CLR)](../dotnet/collection-adapter-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)|Designa la interfaz BCL ajustada.|  
|[collection_adapter::begin (STL/CLR)](../dotnet/collection-adapter-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[collection_adapter::collection_adapter (STL/CLR)](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|Construye un objeto de adaptador.|  
|[collection_adapter::end (STL/CLR)](../dotnet/collection-adapter-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[collection_adapter::size (STL/CLR)](../dotnet/collection-adapter-size-stl-clr.md)|Cuenta el número de elementos.|  
|[collection_adapter::swap (STL/CLR)](../dotnet/collection-adapter-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)|Reemplaza el identificador BCL almacenado.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice esta clase de plantilla para manipular un contenedor BCL como un contenedor STL/CLR. El `collection_adapter` almacena un identificador a una interfaz BCL, que a su vez controla una secuencia de elementos. A `collection_adapter` objeto `X` devuelve un par de iteradores de entrada `X.begin()` y `X.end()` que se utiliza para visitar los elementos en orden. Algunas de las especializaciones también permiten escribir `X.size()` para determinar la longitud de la secuencia controlada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/adaptador >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)
---
title: Unorderedmap (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: f926b400e1cfa2b7b4649efcd0bac73de1faa062
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap (Clase)
Representa un *mapa*no ordenado, que es una colección de pares clave-valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   typename K,  
   typename V,  
   typename C = std::equal_to<K>  
>  
ref class Map sealed;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `K`  
 Tipo de la clave del par clave-valor.  
  
 `V`  
 Tipo del valor del par clave-valor.  
  
 `C`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, [std:: equal_to\<K >](../standard-library/equal-to-struct.md).  
  
### <a name="remarks"></a>Comentarios  
 Los tipos permitidos son:  
  
-   enteros  
  
-   clase de interfaz ^  
  
-   clase ref pública^  
  
-   value struct  
  
-   clase de enumeración pública  
  
 UnorderedMap es básicamente un contenedor de [std:: unordered_map](../standard-library/unordered-map-class.md) que admite el almacenamiento de tipos en tiempo de ejecución de Windows. Es la implementación concreta de la [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408) y [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) tipos que se pasan a través de interfaces de Windows en tiempo de ejecución. Si intentas usar un tipo Platform::Collections::UnorderedMap en un parámetro o valor devuelto público, se produce el error de compilador C3986. Puedes corregir el error si cambias el tipo del parámetro o el valor devuelto a [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408).  
  
 Para obtener más información, consulte [colecciones](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Unorderedmap](#ctor)|Inicializa una nueva instancia de la clase Map.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Unorderedmap:: Clear](#clear)|Quita todos los pares clave-valor del objeto Map actual.|  
|[Unorderedmap:: First](#first)|Devuelve un iterador que especifica el primer elemento del objeto Map.|  
|[Unorderedmap:: GetView](#getview)|Devuelve una vista de solo lectura del objeto Map actual; es decir, una clase Platform::Collections::UnorderedMapView.|  
|[Unorderedmap:: Haskey](#haskey)|Determina si el objeto Map actual contiene la clave especificada.|  
|[Unorderedmap:: Insert](#insert)|Agrega el par clave-valor especificado al objeto Map actual.|  
|[Unorderedmap:: Lookup](#lookup)|Recupera el elemento en la clave especificada del objeto Map actual.|  
|[Unorderedmap:: Remove](#remove)|Elimina el par clave-valor especificado del objeto Map actual.|  
|[Unorderedmap:: Size](#size)|Devuelve el número de elementos del objeto Map actual.|  
  
### <a name="events"></a>Eventos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[Mapchanged](#mapchanged)`event`|Se produce cuando cambia la asignación.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `UnorderedMap`  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  

## <a name="clear"></a>Unorderedmap:: Clear (método)
Quita todos los pares clave-valor del objeto UnorderedMap actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
virtual void Clear();   
```  
  


## <a name="first"></a>Unorderedmap:: First (método)
Devuelve un iterador que especifica el primer [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elemento del mapa no ordenado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que especifica el primer elemento del mapa.  
  
### <a name="remarks"></a>Comentarios  
 Una manera cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myUnorderedMap->First();`.  
  


## <a name="getview"></a>Método unorderedmap:: GetView
Devuelve una vista de solo lectura de UnorderedMap actual; es decir, un [unorderedmapview (clase)](../cppcx/platform-collections-unorderedmapview-class.md) que implementa el [Windows::Foundation::Collections::IMapView::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) interfaz.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
Windows::Foundation::Collections::IMapView<K, V>^   
   GetView();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto `UnorderedMapView`.  
  


## <a name="haskey"></a>Unorderedmap:: Haskey (método)
Determina si el objeto UnorderedMap actual contiene la clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
bool HasKey(  
   K key  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave usada para buscar el elemento UnorderedMap. El tipo de `key` es typename *K*.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si se encuentra la clave; de lo contrario, `false`.  
  


## <a name="insert"></a>  UnorderedMap::Insert Method
Agrega el par clave-valor especificado al objeto UnorderedMap actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
virtual bool Insert(  
   K key,   
   V value  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La parte de clave del par clave-valor. El tipo de `key` es typename *K*.  
  
 `value`  
 La parte de valor del par clave-valor. El tipo de `value` es typename *V*.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la clave de un elemento del mapa actual coincide con `key` y la parte de valor de ese elemento se establece en `value`. `false` si ningún elemento existente del objeto Map actual coincide con `key` y los parámetros `key` y `value` se crean en un par clave-valor y se agregan después al objeto UnorderedMap actual.  
  


## <a name="lookup"></a>Unorderedmap:: Lookup (método)
Recupera el valor de tipo V asociado a la clave especificada de tipo K.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
V Lookup(  
   K key  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave usada para buscar un elemento en el objeto UnorderedMap. El tipo de `key` es typename *K*.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.  
  


## <a name="mapchanged"></a>Unorderedmap:: Mapchanged
Se produce cuando un elemento se inserta en el mapa o se quita del mapa.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;  
```  
  
### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 A [MapChangedEventHandler\<K, V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) que contiene información sobre el objeto que provocó el evento y el tipo de cambio producido. Vea también [IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) y [CollectionChange (enumeración)](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 Aplicaciones de la tienda de Windows que nos C# o Visual Basic proyecto IMap\<K, V > como IDictionary\<K, V >.  
  


## <a name="remove"></a>Unorderedmap:: Remove (método)
Elimina el par clave-valor especificado del objeto UnorderedMap.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
virtual void Remove(  
   K key);  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La parte de clave del par clave-valor. El tipo de `key` es typename *K*.  
  


## <a name="size"></a>Unorderedmap:: Size (método)
Devuelve el número de [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementos de UnorderedMap.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos del objeto UnorderedMap.  
  


## <a name="ctor"></a>  UnorderedMap::UnorderedMap (Constructor)
Inicializa una nueva instancia de la clase UnorderedMap.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
UnorderedMap();  
  
  explicit UnorderedMap(  
      size_t n  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  explicit UnorderedMap(  
      const std::unordered_map<K, V, H, P>& m  
      );  
  
  explicit UnorderedMap(  
      std::unordered_map<K, V, H, P>&& m  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  UnorderedMap(std::initializer_list<  
      std::pair<const K, V>> il  
      );  
  
  UnorderedMap(::std::initializer_list<  
      std::pair<const K, V>> il,  
      size_t n  
      );  
  
  UnorderedMap(  
      ::std::initializer_list< ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(::std::initializer_list<  
      ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
```  
  
### <a name="parameters"></a>Parámetros  
 `InIt`  
 El typename del objeto UnorderedMap actual.  
  
 `P`  
 Un objeto de función que puede comparar dos claves para determinar si son iguales. Este parámetro tiene como valor predeterminado [std:: equal_to\<K >](../standard-library/equal-to-struct.md).  
  
 `H`  
 Un objeto de función que genera un valor hash para una clave. Este parámetro tiene como valor predeterminado [hash clase 1](../standard-library/hash-class.md) para los tipos de clave que admite esa clase.  
  
 `m`  
 Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a una [std:: unordered_map](../standard-library/unordered-map-class.md) que se usa para inicializar el objeto UnorderedMap actual.  
  
 il  
 A [std:: initializer_list](../standard-library/initializer-list-class.md) de [std:: Pair](../standard-library/pair-structure.md)objetos que se usarán para inicializar el objeto map.  
  
 `first`  
 El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.  
  
 `last`  
 El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.  
  


  
## <a name="see-also"></a>Vea también  
 [Namespace de plataforma](platform-namespace-c-cx.md)   
 [Namespace Platform:: Collections](../cppcx/platform-collections-namespace.md)   
 [Clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md)   
 [Unorderedmapview (clase)](../cppcx/platform-collections-unorderedmapview-class.md)   
 [Colecciones](../cppcx/collections-c-cx.md)   
 [Crear componentes de Windows en tiempo de ejecución en C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)
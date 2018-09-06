---
title: Mapview (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
dev_langs:
- C++
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e1dfbcff7e9e470992b0799aac1c87984b52ed50
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755913"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView (Clase)
Representa una vista de solo lectura en un *mapa*, que es una colección de pares clave-valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>>  
ref class MapView sealed;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `K`  
 Tipo de la clave del par clave-valor.  
  
 `V`  
 Tipo del valor del par clave-valor.  
  
 `C`  
 Un tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto MapView. De forma predeterminada, [std:: less\<K >](../standard-library/less-struct.md).  
  
### <a name="remarks"></a>Comentarios  
 MapView es la implementación concreta en C++ de la [Windows::Foundation::Collections::IMapView \<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interfaz que se pasa a través de la interfaz binaria de aplicación (ABI). Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Mapview](#ctor)|Inicializa una nueva instancia de la clase MapView.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Mapview](#first)|Devuelve un iterador que se inicializa el primer elemento en la vista de mapa.|  
|[MapView::HasKey](#haskey)|Determina si el objeto MapView actual contiene la clave especificada.|  
|[Mapview](#lookup)|Recupera el elemento en la clave especificada del objeto MapView actual.|  
|[Mapview](#size)|Devuelve el número de elementos del objeto MapView actual.|  
|[Mapview](#split)|Divide un objeto MapView original en dos objetos MapView.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `MapView`  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  


## <a name="first"></a> Mapview (método)
Devuelve un iterador que especifica el primer elemento de la vista de mapa.  
  
### <a name="syntax"></a>Sintaxis  
  
```    
virtual Windows::Foundation::Collections::IIterator<  
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que especifica el primer elemento de la vista de mapa.  
  
### <a name="remarks"></a>Comentarios  
 Una manera cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myMapView->First();`.  
  


## <a name="haskey"></a>  Haskey (método)
Determina si el objeto MapView actual contiene la clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave que se usa para ubicar el elemento MapView. El tipo de `key` es typename *K*.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si se encuentra la clave; de lo contrario, `false`.  
  


##  <a name="lookup"></a> Mapview (método)
Recupera el valor de tipo V asociado a la clave especificada de tipo K.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave utilizada para buscar un elemento en el objeto MapView. El tipo de `key` es typename *K*.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.  
  


##  <a name="ctor"></a> Constructor Mapview
Inicializa una nueva instancia de la clase MapView.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
explicit MapView(const C& comp = C());  
  
explicit MapView(const ::std::map<K, V, C>& m);  
  
explicit MapView(std::map<K, V, C>&& m);  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C());  
  
MapView(
    ::std::initializer_list<std::pair<const K, V>> il,  
    const C& comp = C());  
```  
  
### <a name="parameters"></a>Parámetros  
 `InIt`  
 El typename del objeto MapView actual.  
  
 `comp`  
 Objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto MapView.  
  
 `m`  
 Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un `map Class` que se usa para inicializar el objeto MapView actual.  
  
 `first`  
 El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto MapView actual.  
  
 `last`  
 El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto MapView actual.  
  
 il  
 Un [std:: initializer_list < std:: Pair\<K, V >>](../standard-library/initializer-list-class.md) cuyos elementos se insertará en el objeto MapView.  



##  <a name="size"></a> Mapview (método)
Devuelve el número de elementos del objeto MapView actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos del objeto MapView actual.  
  


##  <a name="split"></a> Mapview (método)
Divide el objeto MapView actual en dos objetos MapView. Este método no es operativo.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>Parámetros  
 `firstPartition`  
 La primera parte del objeto MapView original.  
  
 `secondPartition`  
 La segunda parte del objeto MapView original.  
  
### <a name="remarks"></a>Comentarios  
 Este método no es operativo; no realiza ninguna acción.  
    
## <a name="see-also"></a>Vea también  
 [Plataforma Namespace](platform-namespace-c-cx.md)
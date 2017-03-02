---
title: Clase CSimpleMap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CSimpleMap
- ATL.CSimpleMap
- CSimpleMap
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: c02ef1d9d3fafebf38abaaa55d77511f4476a02f
ms.lasthandoff: 02/24/2017

---
# <a name="csimplemap-class"></a>Clase CSimpleMap
Esta clase proporciona compatibilidad para una matriz de asignación simple.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>  
class CSimpleMap
```  
  
#### <a name="parameters"></a>Parámetros  
 `TKey`  
 El tipo de elemento de la clave.  
  
 `TVal`  
 El tipo de elemento de valor.  
  
 `TEqual`  
 Un objeto de rasgo, definiendo la prueba de igualdad para los elementos de tipo `T`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|TypeDef para el tipo de valor.|  
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|TypeDef para el tipo de clave.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleMap::CSimpleMap](#csimplemap)|El constructor.|  
|[CSimpleMap:: ~ CSimpleMap](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleMap::Add](#add)|Agrega una clave y un valor asociado a la matriz de asignaciones.|  
|[CSimpleMap::FindKey](#findkey)|Busca una clave específica.|  
|[CSimpleMap::FindVal](#findval)|Busca un valor específico.|  
|[CSimpleMap::GetKeyAt](#getkeyat)|Recupera la clave especificada.|  
|[CSimpleMap::GetSize](#getsize)|Devuelve el número de entradas de la matriz de asignación.|  
|[CSimpleMap::GetValueAt](#getvalueat)|Recupera el valor especificado.|  
|[CSimpleMap::Lookup](#lookup)|Devuelve el valor asociado con la clave especificada.|  
|[CSimpleMap::Remove](#remove)|Quita una clave y un valor coincidente.|  
|[CSimpleMap::RemoveAll](#removeall)|Quita todas las claves y valores.|  
|[CSimpleMap::RemoveAt](#removeat)|Quita una clave específica y un valor coincidente.|  
|[CSimpleMap::ReverseLookup](#reverselookup)|Devuelve la clave asociada con el valor especificado.|  
|[CSimpleMap::SetAt](#setat)|Establece el valor asociado con la clave especificada.|  
|[CSimpleMap::SetAtIndex](#setatindex)|Establece la clave y valor específicos.|  
  
## <a name="remarks"></a>Comentarios  
 `CSimpleMap`proporciona compatibilidad para una matriz de asignación simple de un tipo dado `T`, administración de una matriz no ordenada de elementos clave y sus valores asociados.  
  
 El parámetro `TEqual` proporciona un medio para definir una función de la igualdad de dos elementos de tipo `T`. Al crear una clase similar a [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), es posible modificar el comportamiento de la prueba de igualdad para cualquier matriz determinado. Por ejemplo, cuando se trabaja con una matriz de punteros, puede ser útil definir la igualdad como según los valores que hacen referencia a los punteros. La implementación predeterminada usa **operator==()**.  
  
 Ambos `CSimpleMap` y [CSimpleArray](../../atl/reference/csimplearray-class.md) se proporcionan por compatibilidad con ATL anterior se libera y proporcionan implementaciones de colección más eficaz y completa [CAtlArray](../../atl/reference/catlarray-class.md) y [CAtlMap](../../atl/reference/catlmap-class.md).  
  
 A diferencia de otras colecciones de mapa en ATL y MFC, esta clase se implementa con una simple matriz y búsquedas de búsqueda requieren una búsqueda lineal. `CAtlMap`debe usarse cuando la matriz contiene un gran número de elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#91;](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]  
  
##  <a name="a-nameadda--csimplemapadd"></a><a name="add"></a>CSimpleMap::Add  
 Agrega una clave y un valor asociado a la matriz de asignaciones.  
  
```
BOOL Add(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
 *Val*  
 El valor asociado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la clave y valor se ha agregado correctamente, FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cada par de clave y valor agregado hace que la asignación de memoria se libera y vuelve a asignar, para garantizar que los datos para cada siempre se almacenan de forma contigua de matriz. Es decir, el segundo elemento clave siempre sigue directamente el primer elemento clave en la memoria y así sucesivamente.  
  
##  <a name="a-namearrayelementtypea--csimplemaparrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType  
 Definición de tipos para el tipo de clave.  
  
```
typedef TVal _ArrayElementType;
```  
  
##  <a name="a-namearraykeytypea--csimplemaparraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType  
 Definición de tipos para el tipo de valor.  
  
```
typedef TKey _ArrayKeyType;
```  
  
##  <a name="a-namecsimplemapa--csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap  
 El constructor.  
  
```
CSimpleMap();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa a los miembros de datos.  
  
##  <a name="a-namedtora--csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap:: ~ CSimpleMap  
 Destructor.  
  
```
~CSimpleMap();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="a-namefindkeya--csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey  
 Busca una clave específica.  
  
```
int FindKey(const TKey& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el índice de la clave si se encuentra, de lo contrario, devuelve -1.  
  
##  <a name="a-namefindvala--csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal  
 Busca un valor específico.  
  
```
int FindVal(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *Val*  
 El valor que desea buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve que el índice del valor si se encuentra, en caso contrario, devuelve -1.  
  
##  <a name="a-namegetkeyata--csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyAt  
 Recupera la clave en el índice especificado.  
  
```
TKey& GetKeyAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice de la clave que se va a devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la clave que hace referencia a `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 El índice se pasa `nIndex` debe ser válido para el valor devuelto sea significativo.  
  
##  <a name="a-namegetsizea--csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize  
 Devuelve el número de entradas de la matriz de asignación.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de entradas (una clave y valor es una entrada) de la matriz de asignación.  
  
##  <a name="a-namegetvalueata--csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt  
 Recupera el valor en el índice especificado.  
  
```
TVal& GetValueAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice del valor que se va a devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor al que hace referencia `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 El índice se pasa `nIndex` debe ser válido para el valor devuelto sea significativo.  
  
##  <a name="a-namelookupa--csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Lookup  
 Devuelve el valor asociado con la clave especificada.  
  
```
TVal Lookup(const TKey& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor asociado. Se devuelve si ninguna clave coincidente se encuentra, NULL.  
  
##  <a name="a-nameremovea--csimplemapremove"></a><a name="remove"></a>CSimpleMap::Remove  
 Quita una clave y un valor coincidente.  
  
```
BOOL Remove(const TKey& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la clave y valor coincidente, se ha quitado correctamente, FALSE en caso contrario.  
  
##  <a name="a-nameremovealla--csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::RemoveAll  
 Quita todas las claves y valores.  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita todas las claves y valores del objeto de matriz de asignación.  
  
##  <a name="a-nameremoveata--csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::RemoveAt  
 Quita una clave y un valor asociado en el índice especificado.  
  
```
BOOL RemoveAt(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice de la clave y el valor asociado a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE si el índice especificado es un índice no válido.  
  
##  <a name="a-namereverselookupa--csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::ReverseLookup  
 Devuelve la clave asociada con el valor especificado.  
  
```
TKey ReverseLookup(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *Val*  
 Valor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la clave asociada. Se devuelve si ninguna clave coincidente se encuentra, NULL.  
  
##  <a name="a-namesetata--csimplemapsetat"></a><a name="setat"></a>CSimpleMap::SetAt  
 Establece el valor asociado con la clave especificada.  
  
```
BOOL SetAt(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
 *Val*  
 Nuevo valor que se va a asignar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se encontró la clave y el valor se cambió correctamente.  
  
##  <a name="a-namesetatindexa--csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetAtIndex  
 Establece la clave y valor en un índice especificado.  
  
```
BOOL SetAtIndex(  
    int nIndex,
    const TKey& key,
    const TVal& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice hace referencia a la clave y valor para cambiar de emparejamiento.  
  
 `key`  
 La nueva clave.  
  
 *Val*  
 Nuevo valor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si es correcto, FALSE si el índice no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Actualiza la clave y el valor al que apunta `nIndex`.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)


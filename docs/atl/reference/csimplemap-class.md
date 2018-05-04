---
title: Clase CSimpleMap | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 415ce3c0d6b060ffc71aa448656cf9ad45a3e7bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
 Un objeto de rasgo, definiendo la prueba de igualdad para los elementos del tipo `T`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Definición de tipos para el tipo de valor.|  
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Definición de tipos para el tipo de clave.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMap::CSimpleMap](#csimplemap)|El constructor.|  
|[CSimpleMap:: ~ CSimpleMap](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMap::Add](#add)|Agrega una clave y un valor asociado a la matriz de mapa.|  
|[CSimpleMap::FindKey](#findkey)|Busca una clave específica.|  
|[CSimpleMap::FindVal](#findval)|Busca un valor específico.|  
|[CSimpleMap::GetKeyAt](#getkeyat)|Recupera la clave especificada.|  
|[CSimpleMap::GetSize](#getsize)|Devuelve el número de entradas de la matriz de asignación.|  
|[CSimpleMap::GetValueAt](#getvalueat)|Recupera el valor especificado.|  
|[CSimpleMap::Lookup](#lookup)|Devuelve el valor asociado a la clave dada.|  
|[CSimpleMap::Remove](#remove)|Quita una clave y un valor coincidente.|  
|[CSimpleMap::RemoveAll](#removeall)|Quita todas las claves y valores.|  
|[CSimpleMap::RemoveAt](#removeat)|Quita una clave específica y un valor coincidente.|  
|[CSimpleMap::ReverseLookup](#reverselookup)|Devuelve la clave asociada con el valor dado.|  
|[CSimpleMap::SetAt](#setat)|Establece el valor asociado a la clave dada.|  
|[CSimpleMap::SetAtIndex](#setatindex)|Establece la clave y valor específicos.|  
  
## <a name="remarks"></a>Comentarios  
 `CSimpleMap` proporciona compatibilidad para una matriz de asignación simple de un determinado tipo `T`, administración de una matriz no ordenada de elementos clave y sus valores asociados.  
  
 El parámetro `TEqual` proporciona un medio para definir una función de la igualdad de dos elementos de tipo `T`. Mediante la creación de una clase similar a [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), es posible modificar el comportamiento de la prueba de igualdad para cualquier matriz determinada. Por ejemplo, cuando se trabaja con una matriz de punteros, puede ser útil definir la igualdad como función de los valores que hacen referencia a los punteros. La implementación predeterminada usa **operator==()**.  
  
 Ambos `CSimpleMap` y [CSimpleArray](../../atl/reference/csimplearray-class.md) se proporcionan por compatibilidad con ATL anterior libera y se proporcionan implementaciones de la colección más completo y eficaz con [CAtlArray](../../atl/reference/catlarray-class.md) y [ CAtlMap](../../atl/reference/catlmap-class.md).  
  
 A diferencia de otras colecciones de mapa en MFC y ATL, esta clase se implementa con una matriz simple y búsquedas de búsqueda requieren una búsqueda lineal. `CAtlMap` debe utilizarse cuando la matriz contiene un gran número de elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]  
  
##  <a name="add"></a>  CSimpleMap::Add  
 Agrega una clave y un valor asociado a la matriz de mapa.  
  
```
BOOL Add(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
 *Val*  
 El valor asociado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la clave y valor se agregó correctamente, FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cada par de clave y valor agregado hace que la asignación de memoria se libera y se vuelve a asignar, con el fin de asegurarse de que los datos para cada uno siempre se almacenan de forma contigua de matriz. Es decir, el segundo elemento clave siempre sigue directamente el primer elemento clave en la memoria y así sucesivamente.  
  
##  <a name="_arrayelementtype"></a>  CSimpleMap::_ArrayElementType  
 Una definición de tipo para el tipo de clave.  
  
```
typedef TVal _ArrayElementType;
```  
  
##  <a name="_arraykeytype"></a>  CSimpleMap::_ArrayKeyType  
 Una definición de tipo para el tipo de valor.  
  
```
typedef TKey _ArrayKeyType;
```  
  
##  <a name="csimplemap"></a>  CSimpleMap::CSimpleMap  
 El constructor.  
  
```
CSimpleMap();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa a los miembros de datos.  
  
##  <a name="dtor"></a>  CSimpleMap:: ~ CSimpleMap  
 Destructor.  
  
```
~CSimpleMap();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="findkey"></a>  CSimpleMap::FindKey  
 Busca una clave específica.  
  
```
int FindKey(const TKey& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el índice de la clave si se encuentra, en caso contrario, devuelve -1.  
  
##  <a name="findval"></a>  CSimpleMap::FindVal  
 Busca un valor específico.  
  
```
int FindVal(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *Val*  
 El valor para el que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve que el índice del valor si se encuentra, en caso contrario, devuelve -1.  
  
##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt  
 Recupera la clave en el índice especificado.  
  
```
TKey& GetKeyAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice de la clave que se va a devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la clave que se hace referencia a `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 El índice se pasa `nIndex` debe ser válido para el valor devuelto para que sea significativo.  
  
##  <a name="getsize"></a>  CSimpleMap::GetSize  
 Devuelve el número de entradas de la matriz de asignación.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de entradas (una clave y el valor es una entrada) de la matriz de asignación.  
  
##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt  
 Recupera el valor en el índice especificado.  
  
```
TVal& GetValueAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del valor que se devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor al que hace referencia `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 El índice se pasa `nIndex` debe ser válido para el valor devuelto para que sea significativo.  
  
##  <a name="lookup"></a>  CSimpleMap::Lookup  
 Devuelve el valor asociado a la clave dada.  
  
```
TVal Lookup(const TKey& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor asociado. Si ninguna clave coincidente se encuentra, NULL se devuelve.  
  
##  <a name="remove"></a>  CSimpleMap::Remove  
 Quita una clave y un valor coincidente.  
  
```
BOOL Remove(const TKey& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si la clave y valor coincidente, se han quitado correctamente, FALSE en caso contrario.  
  
##  <a name="removeall"></a>  CSimpleMap::RemoveAll  
 Quita todas las claves y valores.  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita todas las claves y valores del objeto de matriz de asignación.  
  
##  <a name="removeat"></a>  CSimpleMap::RemoveAt  
 Quita una clave y un valor asociado en el índice especificado.  
  
```
BOOL RemoveAt(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice de la clave y el valor asociado a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE si el índice especificado es un índice no válido.  
  
##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup  
 Devuelve la clave asociada con el valor dado.  
  
```
TKey ReverseLookup(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *Val*  
 Valor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la clave asociada. Si ninguna clave coincidente se encuentra, NULL se devuelve.  
  
##  <a name="setat"></a>  CSimpleMap::SetAt  
 Establece el valor asociado a la clave dada.  
  
```
BOOL SetAt(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave.  
  
 *Val*  
 El nuevo valor que se asigna.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se encontró la clave y el valor se cambió correctamente.  
  
##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex  
 Establece la clave y valor en el índice especificado.  
  
```
BOOL SetAtIndex(  
    int nIndex,
    const TKey& key,
    const TVal& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice, que hacen referencia a la clave y valor para cambiar el emparejamiento.  
  
 `key`  
 La nueva clave.  
  
 *Val*  
 Nuevo valor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se realiza correctamente, y FALSE si el índice no era válido.  
  
### <a name="remarks"></a>Comentarios  
 Actualiza la clave y el valor al que señala `nIndex`.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)

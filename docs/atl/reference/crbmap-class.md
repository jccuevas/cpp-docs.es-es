---
title: Clase CRBMap | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b32b21c8785bb5e28058c51f2345c5ffcb6de1f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364942"
---
# <a name="crbmap-class"></a>Clase CRBMap
Esta clase representa una estructura de asignación, utilizando un árbol binario rojo y negro.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```    
  
#### <a name="parameters"></a>Parámetros  
 `K`  
 El tipo de elemento de la clave.  
  
 *V*  
 El tipo de elemento de valor.  
  
 `KTraits`  
 El código utilizado para copiar o mover elementos clave. Vea [CElementTraits clase](../../atl/reference/celementtraits-class.md) para obtener más detalles.  
  
 `VTraits`  
 El código utilizado para copiar o mover elementos de valor.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBMap::CRBMap](#crbmap)|El constructor.|  
|[CRBMap:: ~ CRBMap](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|Llamar a este método para buscar las claves o valores en la `CRBMap` objeto.|  
|[CRBMap::RemoveKey](#removekey)|Llamar a este método para quitar un elemento de la `CRBMap` objeto, la clave dada.|  
|[CRBMap::SetAt](#setat)|Llamar a este método para insertar un par de elementos en el mapa.|  
  
## <a name="remarks"></a>Comentarios  
 `CRBMap` proporciona compatibilidad para una matriz de asignación de un tipo dado, administración de una matriz ordenada de elementos clave y sus valores asociados. Cada clave puede tener solo un valor asociado. Elementos (que consta de una clave y un valor) se almacenan en un árbol binario de la estructura, utilizando la [CRBMap::SetAt](#setat) método. Se pueden quitar elementos mediante el [CRBMap::RemoveKey](#removekey) método, que elimina el elemento con el valor de clave especificado.  
  
 Recorrer el árbol de trabajo se realiza con métodos como [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), y [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).  
  
 El `KTraits` y `VTraits` parámetros son las clases de rasgos que contienen cualquier código complementario necesario para copiar o mover elementos.  
  
 `CRBMap` se deriva de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario mediante el algoritmo de color rojo y negro. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) es una variación que permite varios valores para cada clave. También se deriva de `CRBTree`y por lo que comparte muchas características con `CRBMap`.  
  
 Una alternativa a ambos `CRBMap` y `CRBMultiMap` ofrece la [CAtlMap](../../atl/reference/catlmap-class.md) clase. Cuando solo un pequeño número de elementos tiene que almacenarse, considere el uso de la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase en su lugar.  
  
 Para obtener una explicación más completa de las diversas clases de colección y sus funciones y características de rendimiento, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="crbmap"></a>  CRBMap::CRBMap  
 El constructor.  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 El tamaño del bloque.  
  
### <a name="remarks"></a>Comentarios  
 El `nBlockSize` parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Bloques más grandes, reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos. El valor predeterminado asigna espacio de 10 elementos a la vez.  
  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>  CRBMap:: ~ CRBMap  
 Destructor.  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos asignados.  
  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
##  <a name="lookup"></a>  CRBMap::Lookup  
 Llamar a este método para buscar las claves o valores en la `CRBMap` objeto.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Especifica la clave que identifica el elemento que se va a buscar.  
  
 *valor*  
 Variable que recibe el valor buscado.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer formulario del método devuelve true si se encuentra la clave, en caso contrario, false. Los formularios de la segundo y terceros devuelven un puntero a un [CPair](crbtree-class.md#cpair_class).  
  
### <a name="remarks"></a>Comentarios  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>  CRBMap::RemoveKey  
 Llamar a este método para quitar un elemento de la `CRBMap` objeto, la clave dada.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave correspondiente para el par de elementos que desea quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la clave se encuentra y quita, false en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>  CRBMap::SetAt  
 Llamar a este método para insertar un par de elementos en el mapa.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 El valor de clave para agregar a la `CRBMap` objeto.  
  
 *valor*  
 El valor para agregar a la `CRBMap` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del par clave/valor elemento en el `CRBMap` objeto.  
  
### <a name="remarks"></a>Comentarios  
 `SetAt` reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave/valor.  
  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase CRBTree](../../atl/reference/crbtree-class.md)   
 [Clase de CAtlMap](../../atl/reference/catlmap-class.md)   
 [Clase CRBMultiMap](../../atl/reference/crbmultimap-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

---
title: Clase CRBMap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7b1cd9e54a18746e26929e9768a990bbe0ba6553
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="crbmap-class"></a>Clase CRBMap
Esta clase representa una estructura de asignación, con un árbol binario de rojo-negro.  
  
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
 El código utilizado para copiar o mover elementos clave. Consulte [CElementTraits clase](../../atl/reference/celementtraits-class.md) para obtener más detalles.  
  
 `VTraits`  
 El código utilizado para copiar o mover elementos de valor.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRBMap::CRBMap](#crbmap)|El constructor.|  
|[CRBMap:: ~ CRBMap](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|Llamar a este método para buscar las claves o valores de la `CRBMap` objeto.|  
|[CRBMap::RemoveKey](#removekey)|Llamar a este método para quitar un elemento de la `CRBMap` objeto, dada la clave.|  
|[CRBMap::SetAt](#setat)|Llamar a este método para insertar un par de elementos en el mapa.|  
  
## <a name="remarks"></a>Comentarios  
 `CRBMap`proporciona compatibilidad para una matriz de asignación de un tipo dado, administración de una matriz ordenada de elementos clave y sus valores asociados. Cada clave puede tener solo un valor asociado. Elementos (que consta de una clave y un valor) se almacenan en un árbol binario estructura, utilizando la [CRBMap::SetAt](#setat) método. Se pueden quitar elementos con el [CRBMap::RemoveKey](#removekey) método, que elimina el elemento con el valor de clave especificado.  
  
 Recorrer el árbol se hace posible con métodos como [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), y [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).  
  
 El `KTraits` y `VTraits` parámetros son clases de rasgos que contiene código adicional necesario para copiar o mover elementos.  
  
 `CRBMap`se deriva de [CRBTree](../../atl/reference/crbtree-class.md), que implementa un árbol binario mediante el algoritmo rojo-negro. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) es una variación que permite varios valores para cada clave. También se deriva de `CRBTree`y por lo tanto comparte muchas características con `CRBMap`.  
  
 Una alternativa a ambos `CRBMap` y `CRBMultiMap` ofrecida por la [CAtlMap](../../atl/reference/catlmap-class.md) clase. Cuando se debe almacenar sólo un pequeño número de elementos, considere el uso de la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase en su lugar.  
  
 Para obtener una explicación más completa de las diversas clases de colección y sus funciones y características de rendimiento, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="crbmap"></a>CRBMap::CRBMap  
 El constructor.  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 El tamaño del bloque.  
  
### <a name="remarks"></a>Comentarios  
 El `nBlockSize` parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayores tamaños de bloque reducen las llamadas a rutinas de asignación de memoria, pero utilizan más recursos. El valor predeterminado asigna espacio de 10 elementos a la vez.  
  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#81;](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMap:: ~ CRBMap  
 Destructor.  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos asignados.  
  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
##  <a name="lookup"></a>CRBMap::Lookup  
 Llamar a este método para buscar las claves o valores de la `CRBMap` objeto.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Especifica la clave que identifica el elemento que se va a buscar.  
  
 *value*  
 Variable que recibe el valor buscado.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer formulario del método devuelve true si se encuentra la clave, de lo contrario, false. Los formularios de la segundo y terceros devuelven un puntero a un [CPair](crbtree-class.md#cpair_class).  
  
### <a name="remarks"></a>Comentarios  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#82;](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>CRBMap::RemoveKey  
 Llamar a este método para quitar un elemento de la `CRBMap` objeto, dada la clave.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave correspondiente a la par de elementos que desea quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la clave se encuentra y quita, false en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities número&83;](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>CRBMap::SetAt  
 Llamar a este método para insertar un par de elementos en el mapa.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 El valor de clave para agregar a la `CRBMap` objeto.  
  
 *value*  
 El valor que se va a agregar a la `CRBMap` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del par clave-valor elemento en el `CRBMap` objeto.  
  
### <a name="remarks"></a>Comentarios  
 `SetAt`reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave/valor.  
  
 Consulte la documentación de la clase base [CRBTree](../../atl/reference/crbtree-class.md) para obtener información sobre los métodos disponibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#84;](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase CRBTree](../../atl/reference/crbtree-class.md)   
 [Clase CAtlMap](../../atl/reference/catlmap-class.md)   
 [Clase CRBMultiMap](../../atl/reference/crbmultimap-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)


---
title: Clase CElementTraitsBase | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: 19
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: a06af7698afb24c1c2391b762673c7e3633018d4
ms.lasthandoff: 02/24/2017

---
# <a name="celementtraitsbase-class"></a>Clase CElementTraitsBase
Esta clase proporciona copia de forma predeterminada y move los métodos de una clase de colección.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|Llamar a este método para copiar los elementos almacenados en un objeto de clase de colección.|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|Llame a este método para cambiar la posición de elementos almacenados en un objeto de clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase base define métodos para copiar y reubicación de elementos en una clase de colección. Se utilizan las clases de [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), y [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="copyelements"></a>CElementTraitsBase::CopyElements  
 Llamar a este método para copiar los elementos almacenados en un objeto de clase de colección.  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDest`  
 Puntero al primer elemento que va a recibir los datos copiados.  
  
 `pSrc`  
 Puntero para el primer elemento que se va a copiar.  
  
 `nElements`  
 Número de elementos que se van a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Los elementos de origen y de destino no deben superponerse.  
  
##  <a name="inargtype"></a>CElementTraitsBase::INARGTYPE  
 El tipo de datos que se usará para agregar elementos a la colección.  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de la colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CElementTraitsBase::RelocateElements  
 Llame a este método para cambiar la posición de elementos almacenados en un objeto de clase de colección.  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDest`  
 Puntero al primer elemento que va a recibir los datos trasladados.  
  
 `pSrc`  
 Puntero al primer elemento para cambiar de posición.  
  
 `nElements`  
 El número de elementos que se va a cambiar la posición.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), que es suficiente para la mayoría de los tipos de datos. Si los objetos que se mueven contienen punteros a sus propios miembros, necesitará invalidar este método.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)


---
title: CElementTraitsBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b70ae03c15fcdee4510e25815e516c3e17eb1a2a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879427"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase (clase)
Esta clase proporciona copia de forma predeterminada y move los métodos para una clase de colección.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|Llame a este método para copiar los elementos almacenados en un objeto de clase de colección.|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|Llame a este método para cambiar la posición de elementos almacenados en un objeto de clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase base define métodos para copiar y cambiar la ubicación de los elementos en una clase de colección. Lo utilizan las clases [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), y [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements  
 Llame a este método para copiar los elementos almacenados en un objeto de clase de colección.  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDest*  
 Puntero al primer elemento que va a recibir los datos copiados.  
  
 *pSrc*  
 Puntero en el primer elemento que se va a copiar.  
  
 *nElements*  
 Número de elementos que se van a copiar.  
  
### <a name="remarks"></a>Comentarios  
 No deben superponerse a los elementos de origen y destino.  
  
##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE  
 El tipo de datos que se usará para agregar elementos a la colección.  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de la colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements  
 Llame a este método para cambiar la posición de elementos almacenados en un objeto de clase de colección.  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDest*  
 Puntero al primer elemento que va a recibir los datos trasladados.  
  
 *pSrc*  
 Puntero al primer elemento para cambiar la posición.  
  
 *nElements*  
 El número de elementos que se va a cambiar la ubicación.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), que es suficiente para la mayoría de los tipos de datos. Si los objetos que se está moviendo contienen punteros a sus propios miembros, este método debe invalidarse.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)

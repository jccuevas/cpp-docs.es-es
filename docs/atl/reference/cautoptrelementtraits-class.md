---
title: Clase CAutoPtrElementTraits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c845243e3b99be10af70042688e672fa867fb888
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cautoptrelementtraits-class"></a>Clase CAutoPtrElementTraits
Esta clase proporciona métodos, las funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros inteligentes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CAutoPtrElementTraits 
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```    
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de puntero.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|  
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos, las funciones estáticas y definiciones de tipo para facilitar la la creación de objetos de clase de colección que contiene punteros inteligentes. Las clases de [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) y [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) derivan de `CAutoPtrElementTraits`. Si creando una colección de punteros inteligentes que requiere nuevo vector y operadores de eliminación, utilice [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) en su lugar.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoPtrElementTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="inargtype"></a>  CAutoPtrElementTraits::INARGTYPE  
 El tipo de datos que se usará para agregar elementos al objeto de clase de colección.  
  
```
typedef CAutoPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CAutoPtrElementTraits::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

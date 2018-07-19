---
title: CComQIPtrElementTraits (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e99299d1232fda75d6b0552b5236a060903a08e5
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879657"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits (clase)
Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename I, const IID* piid=& __uuidof(I)>  
class CComQIPtrElementTraits : 
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```  
  
#### <a name="parameters"></a>Parámetros  
 *I*  
 Una interfaz COM que especifica el tipo de puntero que se almacenará.  
  
 *piid*  
 Un puntero para el IID de *me*.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se deriva de los métodos y proporciona una definición de tipo útil al crear una clase de colección de [CComQIPtr](../../atl/reference/ccomqiptr-class.md) objetos de puntero de interfaz COM. Esta clase se utiliza tanto el [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) y [CInterfaceList](../../atl/reference/cinterfacelist-class.md) clases.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="inargtype"></a>  CComQIPtrElementTraits::INARGTYPE  
 El tipo de datos que se usará para agregar elementos al objeto de clase de colección.  
  
```
typedef I* INARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [CDefaultElementTraits (clase)](../../atl/reference/cdefaultelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

---
title: Clase CComQIPtrElementTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: d6405cc3ec04988d0e0d7dd9a98f22c271b3608d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomqiptrelementtraits-class"></a>Clase CComQIPtrElementTraits
Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename I, const IID* piid=& __uuidof(I)>  
class CComQIPtrElementTraits : 
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `I`  
 Una interfaz COM que especifica el tipo de puntero que se almacenará.  
  
 `piid`  
 Un puntero para el IID de `I`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se deriva de métodos y proporciona una definición de tipo útil al crear una clase de colección de [CComQIPtr](../../atl/reference/ccomqiptr-class.md) objetos de puntero de interfaz COM. Esta clase se utiliza tanto la [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) y [CInterfaceList](../../atl/reference/cinterfacelist-class.md) clases.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="inargtype"></a>CComQIPtrElementTraits::INARGTYPE  
 Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.  
  
```
typedef I* INARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)


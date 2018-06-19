---
title: Clase CHeapPtrElementTraits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b29f5893a0b1536a087b0c516e6340eca8449
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360082"
---
# <a name="cheapptrelementtraits-class"></a>Clase CHeapPtrElementTraits
Esta clase proporciona métodos, las funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros del montón.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrElementTraits : 
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de objeto que se almacena en la clase de colección.  
  
 `Allocator`  
 La clase de asignación de memoria utilizada. El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|  
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos, las funciones estáticas y definiciones de tipo para facilitar la la creación de objetos de clase de colección que contiene los punteros del montón. La clase `CHeapPtrList` deriva de `CHeapPtrElementTraits`.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="inargtype"></a>  CHeapPtrElementTraits::INARGTYPE  
 El tipo de datos que se usará para agregar elementos al objeto de clase de colección.  
  
```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CHeapPtrElementTraits::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Clase de plantilla CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

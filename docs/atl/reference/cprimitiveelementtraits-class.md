---
title: CPrimitiveElementTraits (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2219be699e879afb6ec19ad84acc50f18d93a9a9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885814"
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits (clase)
Esta clase proporciona métodos de forma predeterminada y las funciones de una clase de colección formado por tipos de datos primitivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 El tipo de datos que se almacenará en el objeto de clase de colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para mover, copiar, comparar y hash almacenados en un objeto de clase de colección de elementos de tipo de datos primitivos y funciones estáticas de forma predeterminada.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="inargtype"></a>  CPrimitiveElementTraits::INARGTYPE  
 El tipo de datos que se usará para agregar elementos al objeto de clase de colección.  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CPrimitiveElementTraits::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [CDefaultElementTraits (clase)](../../atl/reference/cdefaultelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

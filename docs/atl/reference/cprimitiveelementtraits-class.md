---
title: Clase CPrimitiveElementTraits | Documentos de Microsoft
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
ms.openlocfilehash: 3bec944c4b9a505cc817dbe7aa3ce09a317954f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cprimitiveelementtraits-class"></a>Clase CPrimitiveElementTraits
Esta clase proporciona métodos predeterminados y las funciones de una clase de colección se componen de tipos de datos primitivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacena en el objeto de clase de colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para mover, copiar, comparar y hash almacenados en un objeto de clase de colección de elementos de tipo de datos primitivo y funciones estáticas de forma predeterminada.  
  
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
 [Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

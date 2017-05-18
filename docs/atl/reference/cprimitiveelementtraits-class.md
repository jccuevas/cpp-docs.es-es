---
title: Clase CPrimitiveElementTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
ms.openlocfilehash: 44e3849ebf2de09bc9b62e28df0f70bf52ac95e6
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cprimitiveelementtraits-class"></a>Clase CPrimitiveElementTraits
Esta clase proporciona métodos predeterminados y funciones para una clase de colección se componen de tipos de datos primitivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos se almacenen en el objeto de clase de colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.|  
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
  
##  <a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE  
 Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)


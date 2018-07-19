---
title: CDefaultElementTraits (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c86df573e35ba58d01be6c12ed9fff87c837126
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882668"
---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits (clase)
Esta clase proporciona funciones y métodos predeterminados para una clase de colección.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos y funciones estáticas de forma predeterminada para mover, copiar, comparar y hash elementos almacenados en un objeto de clase de colección. Esta clase deriva sus funciones y métodos de [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md), y [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)y utilizan [ CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md), y [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)

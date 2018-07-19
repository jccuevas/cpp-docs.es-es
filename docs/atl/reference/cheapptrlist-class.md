---
title: CHeapPtrList (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd3342e7c64a13761830073cd3ed82b627b8c407
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879301"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList (clase)
Esta clase proporciona métodos útiles al construir una lista de punteros del montón.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>Parámetros  
 *E*  
 El tipo de objeto que se almacenará en la clase de colección.  
  
 *Asignador*  
 La clase de asignación de memoria que utilice. El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|El constructor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona un constructor y se deriva de los métodos de [CAtlList](../../atl/reference/catllist-class.md) y [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) para facilitar la creación de un objeto de clase de colección almacenar punteros del montón.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList  
 El constructor.  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nBlockSize*  
 El tamaño de bloque.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayor tamaño de bloque reduce las llamadas a rutinas de asignación de memoria, pero usa más recursos.  
  
## <a name="see-also"></a>Vea también  
 [CAtlList (clase)](../../atl/reference/catllist-class.md)   
 [CHeapPtr (clase)](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrElementTraits (clase)](../../atl/reference/cheapptrelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

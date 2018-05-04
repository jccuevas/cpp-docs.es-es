---
title: Clase CAutoPtrList | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9101d66de6782d1a060a8acdfb0d02e9971bb9c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cautoptrlist-class"></a>Clase CAutoPtrList
Esta clase proporciona métodos útiles al construir una lista de punteros inteligentes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename E>  
class CAutoPtrList : 
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `E`  
 El tipo de puntero.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|El constructor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona un constructor y se deriva de métodos de [CAtlList](../../atl/reference/catllist-class.md) y [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) para facilitar la creación de un objeto de lista que almacena los punteros inteligentes. La clase [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) proporciona una función similar para un objeto de matriz.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList  
 El constructor.  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 El tamaño del bloque, su valor predeterminado es 10.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Bloques más grandes, reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlList](../../atl/reference/catllist-class.md)   
 [Clase CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

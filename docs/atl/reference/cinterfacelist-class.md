---
title: CInterfaceList (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33cfcc072e000bc903cceb4ac5551071e35610d9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884381"
---
# <a name="cinterfacelist-class"></a>CInterfaceList (clase)
Esta clase proporciona métodos útiles al construir una lista de punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Parámetros  
 *I*  
 Una interfaz COM que especifica el tipo de puntero que se almacenará.  
  
 *piid*  
 Un puntero para el IID de *me*.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|El constructor de la lista de interfaces.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona un constructor y los métodos derivados para crear una lista de punteros de interfaz COM. Use [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) cuando se requiere una matriz.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList  
 El constructor de la lista de interfaces.  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nBlockSize*  
 El tamaño del bloque, su valor predeterminado es 10.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayor tamaño de bloque reduce las llamadas a rutinas de asignación de memoria, pero usa más recursos.  
  
## <a name="see-also"></a>Vea también  
 [CAtlList (clase)](../../atl/reference/catllist-class.md)   
 [CComQIPtr (clase)](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits (clase)](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

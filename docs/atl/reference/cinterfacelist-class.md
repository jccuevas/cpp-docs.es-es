---
title: Clase CInterfaceList | Documentos de Microsoft
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
ms.openlocfilehash: 1fc523b1eccc88678cda48a0c7e429ea0fc09f9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cinterfacelist-class"></a>Clase CInterfaceList
Esta clase proporciona métodos útiles al construir una lista de punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `I`  
 Una interfaz COM que especifican el tipo de puntero que se almacenará.  
  
 `piid`  
 Un puntero a lo IID de `I`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|El constructor de la lista de interfaces.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos derivadas para crear una lista de punteros de interfaz COM y un constructor. Use [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) cuando se requiere una matriz.  
  
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
 `nBlockSize`  
 El tamaño del bloque, su valor predeterminado es 10.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Bloques más grandes, reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlList](../../atl/reference/catllist-class.md)   
 [Clase CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Clase CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

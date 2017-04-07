---
title: Clase CInterfaceList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 50d86163080c5a0d0a7bb9ed6d77a40ac73722e7
ms.lasthandoff: 02/24/2017

---
# <a name="cinterfacelist-class"></a>Clase CInterfaceList
Esta clase proporciona métodos útiles para construir una lista de punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `I`  
 Una interfaz COM que especifica el tipo de puntero que se almacenará.  
  
 `piid`  
 Un puntero para el IID de `I`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|El constructor de la lista de interfaces.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos derivadas para crear una lista de punteros de interfaz COM y un constructor. Utilice [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) cuando se requiere una matriz.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="cinterfacelist"></a>CInterfaceList::CInterfaceList  
 El constructor de la lista de interfaces.  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 El tamaño del bloque, con un valor predeterminado de 10.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayores tamaños de bloque reducen las llamadas a rutinas de asignación de memoria, pero utilizan más recursos.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlList](../../atl/reference/catllist-class.md)   
 [Clase CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Clase CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)


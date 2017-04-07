---
title: Clase CInterfaceArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
caps.latest.revision: 18
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
ms.openlocfilehash: a2a99eb3cff4f2381d4c58e4d1a7aaa167e83896
ms.lasthandoff: 02/24/2017

---
# <a name="cinterfacearray-class"></a>Clase CInterfaceArray
Esta clase proporciona métodos útiles para construir una matriz de punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|El constructor de la matriz de interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos derivadas para crear una matriz de punteros de interfaz COM y un constructor. Utilice [CInterfaceList](../../atl/reference/cinterfacelist-class.md) cuando se necesita una lista.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="cinterfacearray"></a>CInterfaceArray::CInterfaceArray  
 El constructor.  
  
```
CInterfaceArray() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa la matriz de puntero inteligente.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlArray](../../atl/reference/catlarray-class.md)   
 [Clase CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Clase CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)


---
title: Clase CInterfaceArray | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36a24eadea87d0d34adf0f577b321fa16a7cfc86
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359467"
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
 Una interfaz COM que especifican el tipo de puntero que se almacenará.  
  
 `piid`  
 Un puntero a lo IID de `I`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|El constructor para la matriz de interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona un constructor y los métodos derivados para la creación de una matriz de punteros de interfaz COM. Use [CInterfaceList](../../atl/reference/cinterfacelist-class.md) cuando se requiere una lista.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray  
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
 [Información general de clases](../../atl/atl-class-overview.md)

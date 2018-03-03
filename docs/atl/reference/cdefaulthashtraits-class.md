---
title: Clase CDefaultHashTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2407ffdd5d8ea327cd4669f2c33ccda5e0246d6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdefaulthashtraits-class"></a>Clase CDefaultHashTraits
Esta clase proporciona una función estática para calcular los valores de hash.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CDefaultHashTraits
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDefaultHashTraits::Hash](#hash)|(Estático) Llame a esta función para calcular un valor hash para un elemento determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase contiene una sola función estática que devuelve un valor hash para un elemento determinado. Esta clase se utiliza por la [CDefaultElementTraits clase](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="hash"></a>CDefaultHashTraits::Hash  
 Llame a esta función para calcular un valor hash para un elemento determinado.  
  
```
static ULONG Hash(const T& element) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `element`  
 El elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de hash.  
  
### <a name="remarks"></a>Comentarios  
 El algoritmo hash predeterminado es muy simple: el valor devuelto es el número de elemento. Reemplace esta función si es necesario un algoritmo más complicado.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)

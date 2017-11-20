---
title: Clase CAutoPtrArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs: C++
helpviewer_keywords: CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 952f6a6d9fa06c0f0c34e5769b4302c6230abb43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cautoptrarray-class"></a>Clase CAutoPtrArray
Esta clase proporciona métodos útiles para construir una matriz de punteros inteligentes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `E`  
 El tipo de puntero.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|El constructor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona un constructor y se deriva de métodos de [CAtlArray](../../atl/reference/catlarray-class.md) y [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) para facilitar la creación de un objeto de clase de colección almacenar punteros inteligentes.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray  
 El constructor.  
  
```
CAutoPtrArray() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa la matriz de puntero inteligente.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlArray](../../atl/reference/catlarray-class.md)   
 [Clase CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)   
 [Clase CAutoPtrList](../../atl/reference/cautoptrlist-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

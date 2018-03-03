---
title: Clase CElementTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ebe629a08170ce011b22595c8b821b278e16faa7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="celementtraits-class"></a>Clase CElementTraits
Esta clase se utiliza por las clases de colección para proporcionar las funciones y métodos para mover, copiar, comparación y operaciones hash.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos y funciones estáticas predeterminado para mover, copiar, comparar y hash elementos almacenados en un objeto de clase de colección. `CElementTraits`se especifica como el proveedor predeterminado de estas operaciones mediante las clases de colección [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), y [CRBTree](../../atl/reference/crbtree-class.md).  
  
 Las implementaciones predeterminadas será suficiente para tipos de datos simples, pero si se utilizan las clases de colección para almacenar objetos más complejos, se deben invalidar las funciones y los métodos proporcionados por el usuario las implementaciones.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
## <a name="see-also"></a>Vea también  
 [Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

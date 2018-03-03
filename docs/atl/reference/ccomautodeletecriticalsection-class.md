---
title: Clase CComAutoDeleteCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0a0c5fdd45e819105a3f47e98c02bb5ad3d51be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomautodeletecriticalsection-class"></a>Clase CComAutoDeleteCriticalSection
Esta clase proporciona métodos para la obtención y liberación de propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>Comentarios  
 `CComAutoDeleteCriticalSection`deriva de la clase [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Sin embargo, `CComAutoDeleteCriticalSection` invalida la [término](ccomsafedeletecriticalsection-class.md#term) método `private` acceso, lo que obliga a que se producen cuando las instancias de esta clase salen del ámbito o se eliminan explícitamente de la memoria el Liberador de espacio de memoria interna.  

  
 Esta clase no presenta ningún método adicional a través de su clase base. Vea [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) y [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre las clases de aplicación auxiliar de sección crítica.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
## <a name="see-also"></a>Vea también  
 [Clase CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

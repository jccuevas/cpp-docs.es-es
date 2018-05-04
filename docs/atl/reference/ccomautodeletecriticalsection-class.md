---
title: Clase CComAutoDeleteCriticalSection | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5153520b5a5648f8352465031264c223ffd97c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ccomautodeletecriticalsection-class"></a>Clase CComAutoDeleteCriticalSection
Esta clase proporciona métodos para la obtención y liberación de propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>Comentarios  
 `CComAutoDeleteCriticalSection` deriva de la clase [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Sin embargo, `CComAutoDeleteCriticalSection` invalida la [término](ccomsafedeletecriticalsection-class.md#term) método `private` acceso, lo que obliga a que se producen cuando las instancias de esta clase salen del ámbito o se eliminan explícitamente de la memoria el Liberador de espacio de memoria interna.  

  
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

---
title: CComAutoDeleteCriticalSection (clase) | Microsoft Docs
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
ms.openlocfilehash: 53078d740d1051a928b4592d275f33944685e622
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767109"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection (clase)

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Comentarios

`CComAutoDeleteCriticalSection` se deriva de la clase [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Sin embargo, `CComAutoDeleteCriticalSection` invalida la [término](ccomsafedeletecriticalsection-class.md#term) método **privada** acceso, que fuerza la limpieza de memoria interna que se produzca solo cuando las instancias de esta clase salen del ámbito o se eliminan explícitamente desde memoria.  

Esta clase no presenta ninguna métodos adicionales a través de su clase base. Consulte [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) y [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre las clases auxiliares de sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="see-also"></a>Vea también

[CComSafeDeleteCriticalSection (clase)](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
[CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)

---
title: CComAutoDeleteCriticalSection (clase)
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: d479adce489e0329be3a93b55a70aa3e58a0e038
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246663"
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

[CComSafeDeleteCriticalSection (clase)](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)

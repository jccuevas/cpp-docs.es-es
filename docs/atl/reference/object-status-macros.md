---
title: Macros de estado de objetos
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 5617ce7fb972c98775072f72244f91052d41ece3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326177"
---
# <a name="object-status-macros"></a>Macros de estado de objetos

Esta macro establece indicadores que pertenecen a controles ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Se utiliza en controles ActiveX ATL para establecer los indicadores OLEMISC.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

Se utiliza en controles ActiveX ATL para establecer los indicadores OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parámetros

*miscstatus*<br/>
Todas las marcas OLEMISC aplicables.

### <a name="remarks"></a>Observaciones

Esta macro se utiliza para establecer los indicadores OLEMISC para un control ActiveX. Consulte [IOleObject::GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) para obtener más detalles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)

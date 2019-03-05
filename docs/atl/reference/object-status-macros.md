---
title: Macros de estado de objeto
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: cb5ff6d7570b03b32852fc450f58043446f721f4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267275"
---
# <a name="object-status-macros"></a>Macros de estado de objeto

Esta macro establece marcas que pertenecen a los controles ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Se usa en los controles ActiveX de ATL para establecer las marcas OLEMISC.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS

Se usa en los controles ActiveX de ATL para establecer las marcas OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parámetros

*miscstatus*<br/>
Todos los indicadores OLEMISC.

### <a name="remarks"></a>Comentarios

Esta macro se usa para establecer las marcas OLEMISC para un control ActiveX. Consulte [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) para obtener más detalles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)

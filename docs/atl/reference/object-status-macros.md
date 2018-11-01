---
title: Macros de estado de objeto
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 9c4df80b2b9828077ec3738bc296f19aadf2df68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658957"
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

*MiscStatus*<br/>
Todos los indicadores OLEMISC.

### <a name="remarks"></a>Comentarios

Esta macro se usa para establecer las marcas OLEMISC para un control ActiveX. Consulte [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) para obtener más detalles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)

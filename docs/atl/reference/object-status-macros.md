---
title: Macros de estado de objetos
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: dc50825d6b6e74dc263a097e86d8ea0d42989825
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495317"
---
# <a name="object-status-macros"></a>Macros de estado de objetos

Esta macro establece las marcas que pertenecen a los controles ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Se utiliza en controles ActiveX ATL para establecer las marcas OLEMISC.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS

Se utiliza en controles ActiveX ATL para establecer las marcas OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parámetros

*miscstatus*<br/>
Todas las marcas OLEMISC aplicables.

### <a name="remarks"></a>Comentarios

Esta macro se usa para establecer las marcas OLEMISC para un control ActiveX. Consulte [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) para obtener más información.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)

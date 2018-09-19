---
title: Macros de estado de objeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b684d66a96a7a3a7d7d60a1b107792c2061ce57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086608"
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

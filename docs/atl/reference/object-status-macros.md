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
ms.openlocfilehash: e3657e7076bf67a5a3870d7d127cc150f976ecde
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883663"
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
 *MiscStatus*  
 Todos los indicadores OLEMISC.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se usa para establecer las marcas OLEMISC para un control ActiveX. Consulte [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) para obtener más detalles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

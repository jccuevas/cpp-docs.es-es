---
title: Macros de estado de objeto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs: C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1139c30fa5d23f3320cef76d09fb5bd86c8c4bc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="object-status-macros"></a>Macros de estado de objeto
Esta macro establece marcas que pertenecen a controles ActiveX.  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Usar en controles ActiveX de ATL para establecer el **OLEMISC** marcas.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS  
 Se usa en los controles ActiveX de ATL para establecer las marcas OLEMISC.  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>Parámetros  
 *MiscStatus*  
 Marcas OLEMISC todas aplicables.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se usa para establecer las marcas OLEMISC para un control ActiveX. Hacer referencia a [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) para obtener más detalles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

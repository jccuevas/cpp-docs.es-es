---
title: Funciones globales de contexto de dispositivo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8944ecdb4f9996800264986a7a687df6020b0591
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209938"
---
# <a name="device-context-global-functions"></a>Funciones globales de contexto de dispositivo
Esta función crea un contexto de dispositivo para un dispositivo determinado.  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crea un contexto de dispositivo.|  
  
##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC  
 Crea un contexto de dispositivo para el dispositivo especificado en el [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) estructura.  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>Parámetros  
 *HDC*  
 [in] El identificador existente de un contexto de dispositivo, o NULL.  
  
 *ptd*  
 [in] Un puntero a la `DVTARGETDEVICE` estructura que contiene información sobre el dispositivo de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de contexto de dispositivo para el dispositivo especificado en el `DVTARGETDEVICE`. Si no se especifica ningún dispositivo, devuelve el identificador para el dispositivo de pantalla de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Si la estructura es NULL y *hdc* es NULL, se crea un contexto de dispositivo de la pantalla de forma predeterminada.  
  
 Si *hdc* no es NULL y *ptd* es NULL, la función devuelve existente *hdc*.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
   
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

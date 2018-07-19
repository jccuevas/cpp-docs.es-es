---
title: Macros de mensajes de Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3063dd1bb5bbd9c0eb957b9727027b2d01edfd7d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886211"
---
# <a name="windows-messages-macros"></a>Macros de mensajes de Windows
Esta macro reenvía los mensajes de ventana.  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|Usar para reenviar un mensaje recibido en una ventana a otra ventana para su procesamiento.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG  
 Esta macro reenvía un mensaje recibido en una ventana a otra ventana para su procesamiento.  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha procesado el mensaje, cero si no.  
  
### <a name="remarks"></a>Comentarios  
 Usar WM_FORWARDMSG para reenviar un mensaje recibido en una ventana a otra ventana para su procesamiento. Los parámetros LPARAM y WPARAM se usan como sigue:  
  
|Parámetro|Uso|  
|---------------|-----------|  
|WPARAM|Datos definidos por el usuario|  
|LPARAM|Un puntero a un `MSG` estructura que contiene información acerca de un mensaje|  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, `m_hWndOther` representa la otra ventana que recibe este mensaje.  
  
 [!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

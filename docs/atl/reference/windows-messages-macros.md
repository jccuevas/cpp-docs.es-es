---
title: Macros de mensajes de Windows | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlbase/ATL::WM_FORWARDMSG
dev_langs: C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 66e212b1f8bd2e749bc87fec92b935aa466522b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="windows-messages-macros"></a>Macros de mensajes de Windows
Esta macro reenvía mensajes de ventana.  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|Usar para reenviar un mensaje recibido en una ventana a otra ventana para su procesamiento.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>WM_FORWARDMSG  
 Esta macro reenvía un mensaje recibido en una ventana a otra ventana para su procesamiento.  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha procesado el mensaje, cero si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Use `WM_FORWARDMSG` para reenviar un mensaje recibido en una ventana a otra ventana para su procesamiento. Los parámetros de LPARAM y WPARAM se utilizan como sigue:  
  
|Parámetro|Uso|  
|---------------|-----------|  
|WPARAM|Datos definidos por el usuario|  
|LPARAM|Un puntero a un `MSG` estructura que contiene información acerca de un mensaje|  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, `m_hWndOther` representa la otra ventana que recibe este mensaje.  
  
 [!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

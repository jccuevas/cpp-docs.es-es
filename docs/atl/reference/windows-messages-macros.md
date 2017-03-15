---
title: Macros de mensajes de Windows | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: be814c0a2ade7df8f7a4d6863627e79efe0a48bc
ms.lasthandoff: 02/24/2017

---
# <a name="windows-messages-macros"></a>Macros de mensajes de Windows
Esta macro reenvía los mensajes de ventana.  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|Usar para reenviar un mensaje recibido por una ventana a otra ventana para su procesamiento.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h 
   
##  <a name="a-namewmforwardmsga--wmforwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG  
 Esta macro reenvía un mensaje recibido por una ventana a otra ventana para su procesamiento.  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha procesado el mensaje, cero si no.  
  
### <a name="remarks"></a>Comentarios  
 Use `WM_FORWARDMSG` para reenviar un mensaje recibido por una ventana a otra ventana para su procesamiento. Los parámetros de LPARAM y WPARAM se usan como sigue:  
  
|Parámetro|Uso|  
|---------------|-----------|  
|WPARAM|Datos definidos por el usuario|  
|LPARAM|Un puntero a un `MSG` estructura que contiene información acerca de un mensaje|  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, `m_hWndOther` representa la otra ventana que recibe este mensaje.  
  
 [!code-cpp[NVC_ATL_Windowing&#137;](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)


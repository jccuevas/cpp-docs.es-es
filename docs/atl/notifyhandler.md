---
title: NotifyHandler | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyHandler
dev_langs: C++
helpviewer_keywords: NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11f078e6e47aa6c392de79d9811df8738ce09ed9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="notifyhandler"></a>NotifyHandler
El nombre de la función identificada por el tercer parámetro de la `NOTIFY_HANDLER` macro en el mapa de mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 
    LRESULT 
    NotifyHandler 
 (
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parámetros  
 `idCtrl`  
 El identificador del control que envía el mensaje.  
  
 *pnmh*  
 Dirección de un [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) estructura que contiene el código de notificación e información adicional. Para algunos mensajes de notificación, este parámetro señala a una estructura más grande que tiene el **NMHDR** estructura como su primer miembro.  
  
 `bHandled`  
 Los conjuntos de mapa de mensajes `bHandled` a **TRUE** antes de *NotifyHandler* se llama. Si *NotifyHandler* no controla totalmente el mensaje, se debe establecer `bHandled` a **FALSE** para indicar que el mensaje requiere un procesamiento posterior.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado del procesamiento de mensajes. 0 si es correcto.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).  
  
## <a name="see-also"></a>Vea también  
 [Implementar una ventana](../atl/implementing-a-window.md)   
 [Mapas de mensajes](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)


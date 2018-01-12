---
title: CommandHandler | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CommandHandler
dev_langs: C++
helpviewer_keywords: CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c17d9e731eaee9c6e1a1c584e61db6c9826cf8d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler`es la función identificada por el tercer parámetro de la `COMMAND_HANDLER` macro en el mapa de mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 
    LRESULT 
    CommandHandler 
 (
    WORD wNotifyCode,  
    WORD wID,  
    HWND hWndCtl,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parámetros  
 `wNotifyCode`  
 El código de notificación.  
  
 *wID*  
 El identificador del elemento de menú, control o acelerador.  
  
 *hWndCtl*  
 Un identificador para un control de ventana.  
  
 `bHandled`  
 Los conjuntos de mapa de mensajes `bHandled` a **TRUE** antes de `CommandHandler` se llama. Si `CommandHandler` no controla totalmente el mensaje, se debe establecer `bHandled` a **FALSE** para indicar que el mensaje requiere un procesamiento posterior.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado del procesamiento de mensajes. 0 si es correcto.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).  
  
## <a name="see-also"></a>Vea también  
 [Implementar una ventana](../atl/implementing-a-window.md)   
 [Mapas de mensajes](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)


---
title: MessageHandler | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec0fd88def88f7d31fce078fec0c860f4f21f51c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="messagehandler"></a>MessageHandler
**MessageHandler** es el nombre de la función identificada por el segundo parámetro de la `MESSAGE_HANDLER` macro en el mapa de mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 
    LRESULT 
    MessageHandler 
 (
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parámetros  
 `uMsg`  
 Especifica el mensaje.  
  
 `wParam`  
 Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 Obtener información adicional específica de los mensajes.  
  
 `bHandled`  
 Los conjuntos de mapa de mensajes `bHandled` a **TRUE** antes de `MessageHandler` se llama. Si `MessageHandler` no controla totalmente el mensaje, se debe establecer `bHandled` a **FALSE** para indicar que el mensaje requiere un procesamiento posterior.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado del procesamiento de mensajes. 0 si es correcto.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).  
  
## <a name="see-also"></a>Vea también  
 [Implementar una ventana](../atl/implementing-a-window.md)   
 [Mapas de mensajes](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)


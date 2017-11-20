---
title: MessageHandler | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MessageHandler
dev_langs: C++
helpviewer_keywords: MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd6828f5c6b4f89b7d939e4fd909e72e3039b69f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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


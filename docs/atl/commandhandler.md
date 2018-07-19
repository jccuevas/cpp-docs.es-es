---
title: CommandHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CommandHandler
dev_langs:
- C++
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 784551b090f7c0c73b96b846fcc8d74017cc1e30
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850646"
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler` es la función identificada por el tercer parámetro de la macro COMMAND_HANDLER en el mapa de mensajes.  
  
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
 *wNotifyCode*  
 El código de notificación.  
  
 *wID*  
 El identificador del elemento de menú, control o acelerador.  
  
 *hWndCtl*  
 Identificador de un control de ventana.  
  
 *bHandled*  
 Los conjuntos de mapa de mensajes *bHandled* en TRUE antes de `CommandHandler` se llama. Si `CommandHandler` no controla totalmente el mensaje, se debe establecer *bHandled* en FALSE para indicar que el mensaje requiere un procesamiento posterior.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado del procesamiento de mensajes. 0 si es correcto.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).  
  
## <a name="see-also"></a>Vea también  
 [Implementar una ventana](../atl/implementing-a-window.md)   
 [Mapas de mensajes](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)


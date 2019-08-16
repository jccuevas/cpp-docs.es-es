---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: aa044ef88ba3c872c2652cd774ac50024e52c68c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492321"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`es el nombre de la función identificada por el segundo parámetro de la macro MESSAGE_HANDLER en el mapa de mensajes.

## <a name="syntax"></a>Sintaxis

```
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parámetros

*uMsg*<br/>
Especifica el mensaje.

*wParam*<br/>
Información adicional específica del mensaje.

*lParam*<br/>
Información adicional específica del mensaje.

*bHandled*<br/>
El mapa de mensajes establece *bHandled* en true `MessageHandler` antes de llamar a. Si `MessageHandler` no controla por completo el mensaje, debe establecer *bHandled* en false para indicar que el mensaje necesita más procesamiento.

## <a name="return-value"></a>Valor devuelto

Resultado del procesamiento de mensajes. 0 si se realiza correctamente.

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)<br/>
[Mapas de mensajes](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)

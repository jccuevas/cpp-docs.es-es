---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 99a95228f6036e5f391395be367cdef39ca3dc3b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492454"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler`es la función identificada por el tercer parámetro de la macro COMMAND_HANDLER en el mapa de mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
LRESULT CommandHandler(
    WORD wNotifyCode,
    WORD wID,
    HWND hWndCtl,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parámetros

*wNotifyCode*<br/>
Código de notificación.

*wID*<br/>
Identificador del elemento de menú, control o acelerador.

*hWndCtl*<br/>
Identificador de un control de ventana.

*bHandled*<br/>
El mapa de mensajes establece *bHandled* en true `CommandHandler` antes de llamar a. Si `CommandHandler` no controla por completo el mensaje, debe establecer *bHandled* en false para indicar que el mensaje necesita más procesamiento.

## <a name="return-value"></a>Valor devuelto

Resultado del procesamiento de mensajes. 0 si se realiza correctamente.

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)<br/>
[Mapas de mensajes](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)

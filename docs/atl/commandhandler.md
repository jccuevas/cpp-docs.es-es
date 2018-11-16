---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandHandler
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 8259dfe8ead608876b3637d1dca9c3e808bb419d
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694639"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler` es la función identificada por el tercer parámetro de la macro COMMAND_HANDLER en el mapa de mensajes.

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
El código de notificación.

*wID*<br/>
El identificador del elemento de menú, control o acelerador.

*hWndCtl*<br/>
Identificador de un control de ventana.

*bHandled*<br/>
Los conjuntos de mapa de mensajes *bHandled* en TRUE antes de `CommandHandler` se llama. Si `CommandHandler` no controla totalmente el mensaje, se debe establecer *bHandled* en FALSE para indicar que el mensaje requiere un procesamiento posterior.

## <a name="return-value"></a>Valor devuelto

El resultado del procesamiento de mensajes. 0 si es correcto.

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)<br/>
[Mapas de mensajes](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)


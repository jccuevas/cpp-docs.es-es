---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: d875a039b01b7458a1df46a2539cf5c68aa67e41
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915928"
---
# <a name="notifyhandler"></a>NotifyHandler

El nombre de la función identificada por el tercer parámetro de la macro NOTIFY_HANDLER en el mapa de mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parámetros

*idCtrl*<br/>
Identificador del control que envía el mensaje.

*pnmh*<br/>
Dirección de una estructura [NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr) que contiene el código de notificación e información adicional. En algunos mensajes de notificación, este parámetro apunta a una estructura más grande que `NMHDR` tiene la estructura como primer miembro.

*bHandled*<br/>
El mapa de mensajes establece *bHandled* en true antes de llamar a *NotifyHandler* . Si *NotifyHandler* no controla por completo el mensaje, debe establecer *bHandled* en **false** para indicar que el mensaje necesita más procesamiento.

## <a name="return-value"></a>Valor devuelto

Resultado del procesamiento de mensajes. 0 si se realiza correctamente.

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)<br/>
[Mapas de mensajes](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)

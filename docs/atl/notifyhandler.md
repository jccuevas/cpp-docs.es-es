---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 16fb330d2da83ddfd013e33a2d4b688b2711103b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492296"
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
Dirección de una estructura [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) que contiene el código de notificación e información adicional. En algunos mensajes de notificación, este parámetro apunta a una estructura más grande que `NMHDR` tiene la estructura como primer miembro.

*bHandled*<br/>
El mapa de mensajes establece *bHandled* en true antes de llamar a *NotifyHandler* . Si *NotifyHandler* no controla por completo el mensaje, debe establecer *bHandled* en **false** para indicar que el mensaje necesita más procesamiento.

## <a name="return-value"></a>Valor devuelto

Resultado del procesamiento de mensajes. 0 si se realiza correctamente.

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)<br/>
[Mapas de mensajes](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)

---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NotifyHandler
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 72c8fa3a0773a67c32a0652eb048885564a734be
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694613"
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
El identificador del control que envía el mensaje.

*pnmh*<br/>
Dirección de un [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) estructura que contiene el código de notificación e información adicional. Para algunos mensajes de notificación, este parámetro señala a una estructura más grande que tiene el `NMHDR` estructura como su primer miembro.

*bHandled*<br/>
Los conjuntos de mapa de mensajes *bHandled* en TRUE antes de *NotifyHandler* se llama. Si *NotifyHandler* no controla totalmente el mensaje, se debe establecer *bHandled* a **FALSE** para indicar que el mensaje requiere un procesamiento posterior.

## <a name="return-value"></a>Valor devuelto

El resultado del procesamiento de mensajes. 0 si es correcto.

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)<br/>
[Mapas de mensajes](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)

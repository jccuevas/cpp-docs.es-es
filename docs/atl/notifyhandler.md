---
title: NotifyHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- NotifyHandler
dev_langs:
- C++
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdf9ad03df6a342d47919eb576227422f687d15b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755636"
---
# <a name="notifyhandler"></a>NotifyHandler

El nombre de la función identificada por el tercer parámetro de la macro NOTIFY_HANDLER en el mapa de mensajes.

## <a name="syntax"></a>Sintaxis

```  
LRESULT NotifyHandler(
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parámetros

*idCtrl*  
El identificador del control que envía el mensaje.

*pnmh*  
Dirección de un [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) estructura que contiene el código de notificación e información adicional. Para algunos mensajes de notificación, este parámetro señala a una estructura más grande que tiene el `NMHDR` estructura como su primer miembro.

*bHandled*  
Los conjuntos de mapa de mensajes *bHandled* en TRUE antes de *NotifyHandler* se llama. Si *NotifyHandler* no controla totalmente el mensaje, se debe establecer *bHandled* a **FALSE** para indicar que el mensaje requiere un procesamiento posterior.

## <a name="return-value"></a>Valor devuelto

El resultado del procesamiento de mensajes. 0 si es correcto.

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo del uso de este controlador de mensajes en un mapa de mensajes, vea [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)   
[Mapas de mensajes](../atl/message-maps-atl.md)   
[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

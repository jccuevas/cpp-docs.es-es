---
title: Notificaciones enviadas por los controles de animación
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 2a736e4315091b1b26daceb4fe0ce9672ab33ff6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281270"
---
# <a name="notifications-sent-by-animation-controls"></a>Notificaciones enviadas por los controles de animación

Un control de animación ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) envía dos tipos diferentes de los mensajes de notificación. Las notificaciones se envían en forma de [WM_COMMAND](/windows/desktop/menurc/wm-command) mensajes.

El [mensaje ACN_START](/windows/desktop/Controls/acn-start) mensaje se envía cuando el control de animación ha empezado a reproducirse un clip. El [mensaje ACN_STOP](/windows/desktop/Controls/acn-stop) mensaje se envía cuando el control de animación ha terminado o se detuvo la reproducción un clip.

## <a name="see-also"></a>Vea también

[Uso de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

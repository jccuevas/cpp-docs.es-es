---
title: Notificaciones enviadas por los controles de animación
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: e9e5b94736de44d5cfeef81f5b78a759df3b8aa0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619912"
---
# <a name="notifications-sent-by-animation-controls"></a>Notificaciones enviadas por los controles de animación

Un control de animación ([CAnimateCtrl](reference/canimatectrl-class.md)) envía dos tipos diferentes de mensajes de notificación. Las notificaciones se envían en forma de mensajes de [WM_COMMAND](/windows/win32/menurc/wm-command) .

El mensaje de [ACN_START](/windows/win32/Controls/acn-start) se envía cuando el control de animación ha empezado a reproducir un clip. El mensaje de [ACN_STOP](/windows/win32/Controls/acn-stop) se envía cuando el control de animación finaliza o detiene la reproducción de un clip.

## <a name="see-also"></a>Consulte también

[Usar CAnimateCtrl](using-canimatectrl.md)<br/>
[Permite](controls-mfc.md)

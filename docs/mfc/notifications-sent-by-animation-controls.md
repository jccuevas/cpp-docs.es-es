---
title: Notificaciones enviadas por los controles de animación
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 68ede3bc55669a29eef192d38b29b8c1ab433e4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508023"
---
# <a name="notifications-sent-by-animation-controls"></a>Notificaciones enviadas por los controles de animación

Un control de animación ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) envía dos tipos diferentes de mensajes de notificación. Las notificaciones se envían en forma de mensajes [WM_COMMAND](/windows/win32/menurc/wm-command) .

El mensaje [ACN_START](/windows/win32/Controls/acn-start) se envía cuando el control de animación ha empezado a reproducir un clip. El mensaje [ACN_STOP](/windows/win32/Controls/acn-stop) se envía cuando el control de animación finaliza o detiene la reproducción de un clip.

## <a name="see-also"></a>Vea también

[Uso de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

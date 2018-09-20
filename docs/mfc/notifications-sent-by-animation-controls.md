---
title: Notificaciones enviadas por los controles de animación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb83fe6195c01c1e9dbcc2c00e43738af9ebc8e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386397"
---
# <a name="notifications-sent-by-animation-controls"></a>Notificaciones enviadas por los controles de animación

Un control de animación ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) envía dos tipos diferentes de los mensajes de notificación. Las notificaciones se envían en forma de [WM_COMMAND](/windows/desktop/menurc/wm-command) mensajes.

El [mensaje ACN_START](/windows/desktop/Controls/acn-start) mensaje se envía cuando el control de animación ha empezado a reproducirse un clip. El [mensaje ACN_STOP](/windows/desktop/Controls/acn-stop) mensaje se envía cuando el control de animación ha terminado o se detuvo la reproducción un clip.

## <a name="see-also"></a>Vea también

[Uso de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)


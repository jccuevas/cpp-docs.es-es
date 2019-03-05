---
title: Procesar notificaciones del control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: 3c5d147741123f97a53b18a854db9204738d0a2f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287692"
---
# <a name="processing-header-control-notifications"></a>Procesar notificaciones del control de encabezado

En la clase de vista o cuadro de diálogo, utilice la ventana Propiedades para crear un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) función de controlador con una instrucción switch para cualquier control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) mensajes de notificación que desee controlar (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). Las notificaciones se envían a la ventana primaria cuando el usuario hace clic o hace doble clic en un elemento de encabezado, arrastra un divisor entre elementos y así sucesivamente.

Los mensajes de notificación asociados con un control de encabezado se enumeran en [referencia de Control de encabezado](/windows/desktop/controls/header-control-reference) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

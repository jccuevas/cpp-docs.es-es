---
title: Información sobre herramientas en Windows no derivadas de CFrameWnd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea6f39f8c1478715ecc656ca84c1d6b24b7c03b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445521"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Información sobre herramientas en ventanas no derivadas de CFrameWnd

Esta serie de artículos trata habilitar información sobre herramientas para controles contenidos en una ventana que no se deriva [CFrameWnd](../mfc/reference/cframewnd-class.md). El artículo [información sobre herramientas de las barras de herramientas](../mfc/toolbar-tool-tips.md) proporciona información acerca de la información sobre herramientas para los controles en un `CFrameWnd`.

Los temas tratados en este artículo incluyen:

- [Habilitación de la información sobre herramientas](../mfc/enabling-tool-tips.md)

- [Control de la notificación TTN_NEEDTEXT para la información sobre herramientas](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [TOOLTIPTEXT (estructura)](../mfc/tooltiptext-structure.md)

Información sobre herramientas se muestra automáticamente para los botones y otros controles contenidos en una ventana primaria derivan `CFrameWnd`. Esto es porque `CFrameWnd` tiene un controlador predeterminado para el [notificación TTN_GETDISPINFO](/windows/desktop/Controls/ttn-getdispinfo) notificación, que controla **TTN_NEEDTEXT** notificaciones desde la herramienta sugerencia controles asociados a los controles.

Sin embargo, este controlador predeterminado no se llama cuando el **TTN_NEEDTEXT** notificación se envía desde un control de información sobre herramientas asociado con un control en una ventana que no es un `CFrameWnd`, por ejemplo, un control en un cuadro de diálogo o una vista de formulario. Por lo tanto, es necesario para proporcionar una función de controlador para el **TTN_NEEDTEXT** mensaje de notificación para mostrar información sobre herramientas para los controles secundarios.

La información sobre herramientas predeterminada proporcionada para las ventanas por [CWnd:: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) no tiene texto asociado a ellos. Para recuperar el texto de información sobre herramientas mostrar, el **TTN_NEEDTEXT** se envía una notificación en la ventana principal del control de información sobre herramienta justo antes de mostrar la ventana de información sobre herramientas. Si no hay ningún controlador para este mensaje asignar un valor para el *pszText* miembro de la **TOOLTIPTEXT** estructura, no habrá ningún texto mostrado para la información sobre herramientas.

## <a name="see-also"></a>Vea también

[Información sobre herramientas](../mfc/tool-tips.md)


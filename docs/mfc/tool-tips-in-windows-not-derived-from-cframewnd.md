---
title: Información sobre herramientas en ventanas no derivadas de CFrameWnd
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 1f68fb62335219ea498163e6124c8e91e49f2938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511024"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Información sobre herramientas en ventanas no derivadas de CFrameWnd

En esta familia de artículos se describe cómo habilitar la información sobre herramientas para los controles contenidos en una ventana que no se deriva de [CFrameWnd](../mfc/reference/cframewnd-class.md). En la información sobre herramientas de la [barra de herramientas](../mfc/toolbar-tool-tips.md) de artículos se proporciona información `CFrameWnd`sobre las sugerencias de herramientas para los controles de.

Los temas que se tratan en esta familia de artículos incluyen:

- [Habilitación de la información sobre herramientas](../mfc/enabling-tool-tips.md)

- [Control de la notificación TTN_NEEDTEXT para la información sobre herramientas](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [La estructura TOOLTIPTEXT](../mfc/tooltiptext-structure.md)

La información sobre herramientas se muestra automáticamente para los botones y otros controles contenidos en una ventana `CFrameWnd`primaria derivada de. Esto se debe `CFrameWnd` a que tiene un controlador predeterminado para la notificación [TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo) , que controla las notificaciones **TTN_NEEDTEXT** desde los controles de información sobre herramientas asociados a los controles.

Sin embargo, no se llama a este controlador predeterminado cuando se envía la notificación **TTN_NEEDTEXT** desde un control de información sobre herramientas asociado a un control en una ventana `CFrameWnd`que no es, como un control en un cuadro de diálogo o una vista de formulario. Por lo tanto, es necesario proporcionar una función de controlador para el mensaje de notificación **TTN_NEEDTEXT** con el fin de mostrar la información sobre herramientas para los controles secundarios.

La información sobre herramientas predeterminada proporcionada para las ventanas de [CWnd:: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) no tiene texto asociado. Para recuperar el texto de la información sobre herramientas que se va a mostrar, la notificación **TTN_NEEDTEXT** se envía a la ventana primaria del control de información sobre herramientas justo antes de que se muestre la ventana de información sobre herramientas. Si no hay ningún controlador para este mensaje que asigne algún valor al miembro *miembros pszText* de la estructura **ToolTipText** , no se mostrará ningún texto para la información sobre herramientas.

## <a name="see-also"></a>Vea también

[Información sobre herramientas](../mfc/tool-tips.md)

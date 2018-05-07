---
title: Información sobre herramientas en ventanas no derivadas de CFrameWnd | Documentos de Microsoft
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
ms.openlocfilehash: 34eb8f0b7394828782a3d0f9ed1ca44fb5731af6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Información sobre herramientas en ventanas no derivadas de CFrameWnd
Esta serie de artículos trata habilitar información sobre herramientas para controles contenidos en una ventana que no se deriva de [CFrameWnd](../mfc/reference/cframewnd-class.md). El artículo [información sobre herramientas de las barras de herramientas](../mfc/toolbar-tool-tips.md) proporciona información acerca de la información sobre herramientas para los controles en un `CFrameWnd`.  
  
 Entre los temas tratados en esta serie de artículos se incluyen:  
  
-   [Habilitación de la información sobre herramientas](../mfc/enabling-tool-tips.md)  
  
-   [Control de la notificación TTN_NEEDTEXT para la información sobre herramientas](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [TOOLTIPTEXT (estructura)](../mfc/tooltiptext-structure.md)  
  
 Información sobre herramientas se muestra automáticamente para botones y otros controles de contenido en una ventana primaria que se derivan de `CFrameWnd`. Esto es porque `CFrameWnd` tiene un controlador predeterminado para la [notificación TTN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269) notificación, que administra las **TTN_NEEDTEXT** notificaciones de herramienta sugerencia controles asociados a controles.  
  
 Sin embargo, este controlador predeterminado no se llama cuando el **TTN_NEEDTEXT** notificación se envía desde un control de información sobre herramientas asociado a un control en una ventana que no es un `CFrameWnd`, por ejemplo, un control en un cuadro de diálogo o una vista de formulario. Por lo tanto, es necesario que proporcione una función de controlador para el **TTN_NEEDTEXT** mensaje de notificación para mostrar información sobre herramientas para los controles secundarios.  
  
 La información sobre herramientas predeterminada proporcionada para las ventanas por [CWnd:: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) no tiene texto asociado a ellos. Para recuperar el texto de la información sobre herramientas mostrar, la **TTN_NEEDTEXT** notificación se envía a la ventana primaria del control de información sobre herramienta justo antes de que se muestra la ventana de información sobre herramientas. Si no hay ningún controlador para este mensaje asignar un valor a la **pszText** miembro de la **TOOLTIPTEXT** estructura, no habrá ningún texto de muestra para la información sobre herramientas.  
  
## <a name="see-also"></a>Vea también  
 [Información sobre herramientas](../mfc/tool-tips.md)


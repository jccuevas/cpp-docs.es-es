---
title: Habilitar la información sobre herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: bdd5c54f9174c42e17db0be7e13ea31acfea2dcf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615729"
---
# <a name="enabling-tool-tips"></a>Habilitar la información sobre herramientas

Puede habilitar la compatibilidad con la información sobre herramientas para los controles secundarios de una ventana (como los controles de una vista de formulario o un cuadro de diálogo).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Para habilitar la información sobre herramientas para los controles secundarios de una ventana

1. Llame a `EnableToolTips` para la ventana para la que desea proporcionar información sobre herramientas.

1. Proporcione una cadena para cada control del controlador de [notificación de TTN_NEEDTEXT](handling-ttn-needtext-notification-for-tool-tips.md) . El controlador está en el mapa de mensajes de la ventana que contiene los controles secundarios (por ejemplo, la clase de vista de formulario). Este controlador debe llamar a una función que identifica el control y establece **miembros pszText** para especificar el texto utilizado por el control de información sobre herramientas.

## <a name="see-also"></a>Consulte también

[Información sobre herramientas en ventanas no derivadas de CFrameWnd](tool-tips-in-windows-not-derived-from-cframewnd.md)

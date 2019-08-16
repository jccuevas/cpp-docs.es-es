---
title: Trabajar con el control ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 60cc527493e2a68751c201b998ab171c564d6c1f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510578"
---
# <a name="working-with-the-toolbar-control"></a>Trabajar con el control ToolBar

En este artículo se explica cómo se puede tener acceso al objeto [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) subyacente a [CToolBar](../mfc/reference/ctoolbar-class.md) para tener un mayor control sobre las barras de herramientas. Este es un tema avanzado.

## <a name="procedures"></a>Procedimientos

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Para tener acceso al control común de barra de herramientas subyacente del objeto CToolBar

1. Llame a [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl`Devuelve una referencia a un objeto [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) . Puede utilizar la referencia para llamar a funciones miembro de la clase de control Toolbar.

> [!CAUTION]
>  Aunque llamar `CToolBarCtrl` a funciones **Get** es seguro, tenga cuidado si llama a las funciones de **conjunto** . Este es un tema avanzado. Normalmente no es necesario tener acceso al control de barra de herramientas subyacente.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Controles (controles comunes de Windows)](../mfc/controls-mfc.md)

- [Aspectos básicos de las barras de herramientas](../mfc/toolbar-fundamentals.md)

- [Barras de herramientas de acoplamiento y flotantes](../mfc/docking-and-floating-toolbars.md)

- [Cambiar el tamaño de la barra de herramientas dinámicamente](../mfc/docking-and-floating-toolbars.md)

- [Información sobre herramientas de barra de herramientas](../mfc/toolbar-tool-tips.md)

- [Flyby actualizaciones de la barra de estado](../mfc/toolbar-tool-tips.md)

- [Control de las notificaciones de información sobre herramientas](../mfc/handling-tool-tip-notifications.md)

- Clases [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Control de notificaciones de personalización](../mfc/handling-customization-notifications.md)

- [Varias barras de herramientas](../mfc/toolbar-fundamentals.md)

- [Usar las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)

- [Barras de control](../mfc/control-bars.md)

Para obtener información general sobre el uso de controles comunes de Windows, vea [controles comunes](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Vea también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

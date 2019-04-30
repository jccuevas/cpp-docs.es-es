---
title: Trabajar con el control ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 88c00bf60f2ce1fccecd757d13b2f814e3a18be4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399504"
---
# <a name="working-with-the-toolbar-control"></a>Trabajar con el control ToolBar

En este artículo se explica cómo puede tener acceso a la [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) subyacente del objeto un [CToolBar](../mfc/reference/ctoolbar-class.md) para un mayor control sobre las barras de herramientas. Se trata de un tema avanzado.

## <a name="procedures"></a>Procedimientos

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Para obtener acceso al control común de barra de herramientas subyacente al objeto CToolBar.

1. Llame a [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl` Devuelve una referencia a un [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto. Puede utilizar la referencia para llamar a funciones miembro de la clase de control de barra de herramientas.

> [!CAUTION]
>  Durante la llamada a `CToolBarCtrl` **obtener** funciones es segura, tenga cuidado si se llama a la **establecer** funciones. Se trata de un tema avanzado. Normalmente no es necesario tener acceso al control de barra de herramientas subyacente.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Controles (controles comunes de Windows)](../mfc/controls-mfc.md)

- [Aspectos básicos de la barra de herramientas](../mfc/toolbar-fundamentals.md)

- [Acoplar y desacoplar las barras de herramientas](../mfc/docking-and-floating-toolbars.md)

- [Cambiar el tamaño de la barra de herramientas dinámicamente](../mfc/docking-and-floating-toolbars.md)

- [Información sobre herramientas de barra de herramientas](../mfc/toolbar-tool-tips.md)

- [Actualizaciones de barra de estado por proximidad](../mfc/toolbar-tool-tips.md)

- [Controlar las notificaciones de información sobre herramientas](../mfc/handling-tool-tip-notifications.md)

- El [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) clases

- [Controlar las notificaciones de personalización](../mfc/handling-customization-notifications.md)

- [Varias barras de herramientas](../mfc/toolbar-fundamentals.md)

- [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)

- [Barras de control](../mfc/control-bars.md)

Para obtener información general sobre el uso de controles comunes de Windows, consulte [controles comunes](/windows/desktop/Controls/common-controls-intro).

## <a name="see-also"></a>Vea también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

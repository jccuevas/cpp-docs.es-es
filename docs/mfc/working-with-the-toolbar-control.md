---
title: Trabajar con el control ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 371f1944fae655556bbc9f89d7ffcce7cc326e5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365250"
---
# <a name="working-with-the-toolbar-control"></a>Trabajar con el control ToolBar

En este artículo se explica cómo puede tener acceso a la [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto subyacente a un [CToolBar](../mfc/reference/ctoolbar-class.md) para un mayor control sobre las barras de herramientas. Este es un tema avanzado.

## <a name="procedures"></a>Procedimientos

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Para tener acceso al control común de la barra de herramientas subyacente a su CToolBar objeto

1. Llame a [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl`devuelve una referencia a un [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto. Puede utilizar la referencia para llamar a funciones miembro de la clase de control de barra de herramientas.

> [!CAUTION]
> Mientras `CToolBarCtrl` que llamar a **Get** funciones es seguro, tenga cuidado si llama a la **Set** funciones. Este es un tema avanzado. Normalmente no es necesario tener acceso al control de barra de herramientas subyacente.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Controles (controles comunes de Windows)](../mfc/controls-mfc.md)

- [Fundamentos de la barra de herramientas](../mfc/toolbar-fundamentals.md)

- [Barras de herramientas de acoplamiento y flotantes](../mfc/docking-and-floating-toolbars.md)

- [Cambiar el tamaño dinámico de la barra de herramientas](../mfc/docking-and-floating-toolbars.md)

- [Consejos de herramientas de la barra de herramientas](../mfc/toolbar-tool-tips.md)

- [Actualizaciones de la barra de estado de Flyby](../mfc/toolbar-tool-tips.md)

- [Control de las notificaciones de información sobre herramientas](../mfc/handling-tool-tip-notifications.md)

- Las clases [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Manejo de notificaciones de personalización](../mfc/handling-customization-notifications.md)

- [Múltiples barras de herramientas](../mfc/toolbar-fundamentals.md)

- [Uso de las barras de herramientas antiguas](../mfc/using-your-old-toolbars.md)

- [Barras de control](../mfc/control-bars.md)

Para obtener información general sobre el uso de controles comunes de Windows, vea [Controles comunes](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Consulte también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

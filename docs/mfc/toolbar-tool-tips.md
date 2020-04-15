---
title: Información sobre herramientas de la barra de herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
ms.openlocfilehash: 1762931b75734801659fd6271377260bd0473614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373458"
---
# <a name="toolbar-tool-tips"></a>Información sobre herramientas de la barra de herramientas

Las sugerencias de herramientas son las pequeñas ventanas emergentes que presentan descripciones cortas del propósito de un botón de la barra de herramientas cuando se coloca el ratón sobre un botón durante un período de tiempo. Al crear una aplicación con el Asistente para aplicaciones que tiene una barra de herramientas, se proporciona compatibilidad con información sobre herramientas. En este artículo se explica tanto la compatibilidad con información sobre herramientas creada por el Asistente para aplicaciones como cómo agregar compatibilidad con información sobre herramientas a la aplicación.

En este artículo se describe:

- [Activación de las puntas de las herramientas](#_core_activating_tool_tips)

- [Actualizaciones de la barra de estado de Flyby](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a>Activación de las sugerencias de herramientas

Para activar las sugerencias de herramientas en la aplicación, debe hacer dos cosas:

- Agregue el estilo CBRS_TOOLTIPS a los otros estilos (como WS_CHILD, WS_VISIBLE y otros estilos de **CBRS_)** pasados como el parámetro *dwStyle* a la función [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) o en [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Como se describe en el procedimiento siguiente, anexe el texto de la sugerencia de la barra de herramientas, separado por un carácter de nueva línea ('n'), al recurso de cadena que contiene el símbolo del sistema para el comando de la barra de herramientas. El recurso de cadena comparte el identificador del botón de la barra de herramientas.

#### <a name="to-add-the-tool-tip-text"></a>Para añadir el texto de la información sobre herramientas

1. Mientras edita la barra de herramientas en el editor de la barra de herramientas, abra la ventana Propiedades del **botón** de barra de herramientas para un botón determinado.

1. En el cuadro **Preguntar,** especifique el texto que desea que aparezca en la información sobre herramientas de ese botón.

> [!NOTE]
> Establecer el texto como una propiedad de botón en el editor de la barra de herramientas reemplaza el procedimiento anterior, en el que tenía que abrir y editar el recurso de cadena.

Si una barra de control con las sugerencias de herramientas habilitadas tiene controles secundarios colocados, la barra de control mostrará una información sobre herramientas para cada control secundario en la barra de control, siempre que cumpla los siguientes criterios:

- El ID del control no es - 1.

- La entrada de tabla de cadenas con el mismo identificador que el control secundario en el archivo de recursos tiene una cadena de información sobre herramientas.

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a>Actualizaciones de la barra de estado de Flyby

Una característica relacionada con las sugerencias de herramientas es la actualización de la barra de estado "flyby". De forma predeterminada, el mensaje de la barra de estado describe solo un botón de barra de herramientas determinado cuando se activa el botón. Al incluir CBRS_FLYBY en la `CToolBar::Create`lista de estilos pasados a , puede tener estos mensajes actualizados cuando el cursor del ratón pasa por encima de la barra de herramientas sin activar realmente el botón.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Implementación de la barra de herramientas MFC (información general sobre las barras de herramientas)](../mfc/mfc-toolbar-implementation.md)

- [Barras de herramientas de acoplamiento y flotantes](../mfc/docking-and-floating-toolbars.md)

- Las clases [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Trabajar con el control de la barra de herramientas](../mfc/working-with-the-toolbar-control.md)

- [Uso de las barras de herramientas antiguas](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Consulte también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

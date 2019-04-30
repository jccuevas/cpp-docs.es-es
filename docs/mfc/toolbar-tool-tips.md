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
ms.openlocfilehash: 4582b03844e1be3d4cf70bcc3fff1c3b66119ae3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351779"
---
# <a name="toolbar-tool-tips"></a>Información sobre herramientas de la barra de herramientas

Información sobre herramientas es esa pequeña ventana emergente que muestra una breve descripción del propósito de un botón de barra de herramientas cuando coloca el mouse sobre un botón durante un período de tiempo. Cuando se crea una aplicación con el Asistente para aplicaciones que tiene una barra de herramientas, se proporciona compatibilidad con la sugerencia de herramienta. En este artículo se explica tanto la herramienta compatibilidad con la sugerencia creado por el Asistente para aplicaciones y cómo agregar compatibilidad con la sugerencia de herramienta a la aplicación.

En este artículo se tratan los aspectos siguientes:

- [Información sobre herramientas de activación](#_core_activating_tool_tips)

- [Actualizaciones de barra de estado por proximidad](#_core_fly_by_status_bar_updates)

##  <a name="_core_activating_tool_tips"></a> Información sobre herramientas de activación

Para activar la información sobre herramientas en la aplicación, debe hacer dos cosas:

- Agregar el estilo CBRS_TOOLTIPS a los demás estilos (como WS_CHILD, WS_VISIBLE y otros **CBRS_** estilos) pasa como el *dwStyle* parámetro para el [CToolBar:: Create](../mfc/reference/ctoolbar-class.md#create) función o en [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Como se describe en el procedimiento siguiente, anexe el texto de sugerencia de la barra de herramientas, separado por un carácter de nueva línea ('\n') para el recurso de cadena que contiene el símbolo del sistema de línea de comandos para el comando de barra de herramientas. El recurso de cadena comparte el identificador del botón de barra de herramientas.

#### <a name="to-add-the-tool-tip-text"></a>Para agregar el texto de sugerencia

1. Mientras se edita la barra de herramientas en el editor de la barra de herramientas, abra el **las propiedades del botón de barra de herramientas** ventana de un botón determinado.

1. En el **Prompt** , especifique el texto que desee que aparezca en la información sobre herramientas para ese botón.

> [!NOTE]
>  Define el texto como el procedimiento anterior, en el que tenía que reemplaza a una propiedad en el editor de la barra de herramientas del botón Abrir y editar el recurso de cadena.

Si una barra de controles con información sobre herramientas habilitado tiene controles secundarios se colocan en él, la barra de control mostrará una información sobre herramientas para cada control secundario en la barra de control, siempre cumpla los criterios siguientes:

- El identificador del control es no - 1.

- La entrada de tabla de cadenas con el mismo identificador que el control secundario en el archivo de recursos tiene una cadena de información sobre herramientas.

##  <a name="_core_fly_by_status_bar_updates"></a> Actualizaciones de la barra de estado por proximidad

Una característica relacionada con información sobre herramientas es el estado "por proximidad" actualización de la barra. De forma predeterminada, el mensaje en la barra de estado describe solamente un botón de barra de herramientas cuando se activa el botón. Incluyendo CBRS_FLYBY en la lista de estilos que se pasan a `CToolBar::Create`, debe actualizar estos mensajes cuando el cursor del mouse pasa por encima de la barra de herramientas sin activar realmente el botón.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Implementación de la barra de herramientas de MFC (información general sobre las barras de herramientas)](../mfc/mfc-toolbar-implementation.md)

- [Acoplar y desacoplar las barras de herramientas](../mfc/docking-and-floating-toolbars.md)

- El [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) clases

- [Trabajar con el control de barra de herramientas](../mfc/working-with-the-toolbar-control.md)

- [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Vea también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

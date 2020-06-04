---
title: Barras de controles
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: ceae20c89d9a6d3f4393f838b3594938107785f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353568"
---
# <a name="control-bars"></a>Barras de controles

"Barra de control" es el nombre general de las barras de herramientas, las barras de estado y las barras de diálogo. Clases `CToolBar` `CStatusBar`MFC `CDialogBar` `COleResizeBar`, `CReBar` , , , y derivan de la clase [CControlBar](../mfc/reference/ccontrolbar-class.md), que implementa su funcionalidad común.

Las barras de control son ventanas que muestran filas de controles con las que los usuarios pueden seleccionar opciones, ejecutar comandos u obtener información del programa. Los tipos de barras de control incluyen barras de herramientas, barras de diálogo y barras de estado.

- Barras de herramientas, en la clase [CToolBar](../mfc/reference/ctoolbar-class.md)

- Barras de estado, en la clase [CStatusBar](../mfc/reference/cstatusbar-class.md)

- Barras de diálogo, en la clase [CDialogBar](../mfc/reference/cdialogbar-class.md)

- Rebares, en la clase [CReBar](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
> A partir de la versión 4.0 de MFC, las barras de herramientas, las barras de estado y las sugerencias de herramientas se implementan mediante la funcionalidad del sistema implementada en *comctl32.dll* en lugar de la implementación anterior específica de MFC. En MFC versión `CReBar`6.0, , que también ajusta la funcionalidad comctl32.dll, se agregó.

A continuación se ofrecen breves introducciones a los tipos de barra de control. Para obtener más información, consulte los enlaces a continuación.

## <a name="control-bars"></a>Barras de controles

Las barras de control mejoran en gran medida la facilidad de uso de un programa al proporcionar acciones de comando rápidas y de un solo paso. Clase `CControlBar` proporciona la funcionalidad común de todas las barras de herramientas, barras de estado y barras de diálogo. `CControlBar`proporciona la funcionalidad para colocar la barra de control en su ventana de marco primario. Dado que una barra de control suele ser una ventana secundaria de una ventana de marco principal, es un "hermano" en la vista de cliente o cliente MDI de la ventana de marco. Un objeto de barra de control utiliza información sobre el rectángulo de cliente de su ventana primaria para posicionarse. A continuación, modifica el rectángulo de ventana de cliente restante del elemento primario para que la vista de cliente o la ventana de cliente MDI llene el resto de la ventana de cliente.

> [!NOTE]
> Si un botón de la barra de control no tiene un controlador **COMMAND** o **UPDATE_COMMAND_UI,** el marco de trabajo deshabilita automáticamente el botón.

## <a name="toolbars"></a>Barras de herramientas

Una barra de herramientas es una barra de control que muestra una fila de botones de mapa de bits que llevan a cabo comandos. Presionar un botón de la barra de herramientas equivale a elegir un elemento de menú; llama al mismo controlador asignado a un elemento de menú si ese elemento de menú tiene el mismo identificador que el botón de la barra de herramientas. Los botones se pueden configurar para que aparezcan y se comporten como pulsadores, botones de opción o casillas de verificación. Una barra de herramientas normalmente se alinea con la parte superior de una ventana de marco, pero una barra de herramientas MFC puede "acoplarse" a cualquier lado de su ventana primaria o flotar en su propia ventana de marco pequeño. Una barra de herramientas también puede "flotar" y puede cambiar su tamaño y arrastrarlo con un ratón. Una barra de herramientas también puede mostrar sugerencias de herramientas a medida que el usuario mueve el mouse sobre los botones de la barra de herramientas. Una información sobre herramientas es una pequeña ventana emergente que describe brevemente el propósito del botón.

> [!NOTE]
> A partir de la versión 4.0 de MFC, la clase [CToolBar](../mfc/reference/ctoolbar-class.md) utiliza el control común de la barra de herramientas de Windows. A `CToolBar` contiene un [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Sin embargo, las barras de herramientas más antiguas siguen siendo compatibles. Consulte el artículo [Barras de herramientas](../mfc/mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Barras de estado

Una barra de estado es una barra de control que contiene paneles de salida de texto o "indicadores". Los paneles de salida se utilizan comúnmente como líneas de mensaje y como indicadores de estado. Ejemplos de línea de mensaje incluyen las líneas de mensaje de ayuda de comando que explican brevemente el menú seleccionado o el comando de barra de herramientas en el panel izquierdo de la barra de estado predeterminada creada por el Asistente para aplicaciones MFC. Los ejemplos de indicadores de estado incluyen el BLOQUEO SCROLL, EL BLOQUEO NUM y otras teclas. Las barras de estado suelen estar alineadas con la parte inferior de una ventana de marco. Vea la clase [CStatusBar](../mfc/reference/cstatusbar-class.md) y la clase [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Barras de cuadro de diálogo

Una barra de diálogo es una barra de control, basada en un recurso de plantilla de cuadro de diálogo, con la funcionalidad de un cuadro de diálogo no basado. Las barras de diálogo pueden contener controles Windows, personalizados o ActiveX. Al igual que en un cuadro de diálogo, el usuario puede tabular entre los controles. Las barras de diálogo se pueden alinear con la parte superior, inferior, izquierda o derecha de una ventana de marco y también se pueden flotar en su propia ventana de marco. Vea la clase [CDialogBar](../mfc/reference/cdialogbar-class.md).

## <a name="rebars"></a>Barras de re-barras

Una [armadura](../mfc/using-crebarctrl.md) es una barra de control que proporciona información de acoplamiento, diseño, estado y persistencia para los controles de armadura. Un objeto de armadura puede contener una variedad de ventanas secundarias, normalmente otros controles, incluidos cuadros de edición, barras de herramientas y cuadros de lista. Un objeto de armadura puede mostrar sus ventanas secundarias sobre un mapa de bits especificado. Se puede cambiar de tamaño de forma automática o manual haciendo clic o arrastrando su barra de pinzamiento. Consulte la clase [CReBar](../mfc/reference/crebar-class.md).

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)

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
ms.openlocfilehash: a2d3683b744493bb5566456b9e1358c1ddc418d4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615973"
---
# <a name="control-bars"></a>Barras de controles

"Barra de control" es el nombre general de las barras de herramientas, las barras de estado y las barras de diálogo. Las clases MFC `CToolBar` ,, `CStatusBar` `CDialogBar` , y se `COleResizeBar` `CReBar` derivan de la clase [CControlBar](reference/ccontrolbar-class.md), que implementa su funcionalidad común.

Las barras de control son ventanas que muestran filas de controles con los que los usuarios pueden seleccionar opciones, ejecutar comandos u obtener información del programa. Los tipos de barras de control incluyen barras de herramientas, barras de cuadro de diálogo y barras de estado.

- Barras de herramientas, en la clase [CToolBar](reference/ctoolbar-class.md)

- Barras de estado, en la clase [CStatusBar](reference/cstatusbar-class.md)

- Barras de cuadro de diálogo, en la clase [CDialogBar](reference/cdialogbar-class.md)

- Barras, en la clase [CReBar](reference/crebar-class.md)

> [!IMPORTANT]
> A partir de la versión 4,0 de MFC, las barras de herramientas, las barras de estado y la información sobre herramientas se implementan mediante la funcionalidad del sistema implementada en *COMCTL32. dll* en lugar de la implementación anterior específica de MFC. En la versión 6,0 de MFC, `CReBar` , que también incluye la funcionalidad de COMCTL32. dll, se ha agregado.

A continuación se presentan breves introducciones a los tipos de barra de control. Para obtener más información, vea los vínculos siguientes.

## <a name="control-bars"></a>Barras de controles

Las barras de control mejoran en gran medida la facilidad de uso de un programa, ya que proporcionan acciones rápidas de comandos de un solo paso. `CControlBar`La clase proporciona la funcionalidad común de todas las barras de herramientas, barras de estado y barras de cuadro de diálogo. `CControlBar`proporciona la funcionalidad para colocar la barra de control en su ventana de marco primaria. Dado que una barra de control suele ser una ventana secundaria de una ventana de marco primaria, es un "elemento relacionado" de la vista de cliente o del cliente MDI de la ventana de marco. Un objeto de barra de control usa información sobre el rectángulo de cliente de la ventana primaria para colocarse. A continuación, modifica el rectángulo de la ventana de cliente restante del elemento primario para que la ventana de cliente o la vista de cliente rellene el resto de la ventana de cliente.

> [!NOTE]
> Si un botón de la barra de control no tiene un **comando** o un controlador de **UPDATE_COMMAND_UI** , el marco de trabajo deshabilita automáticamente el botón.

## <a name="toolbars"></a>Barras de herramientas

Una barra de herramientas es una barra de controles que muestra una fila de botones de mapas de filas que llevan a cabo comandos. Presionar un botón de la barra de herramientas equivale a elegir un elemento de menú. llama al mismo controlador asignado a un elemento de menú si ese elemento de menú tiene el mismo identificador que el botón de la barra de herramientas. Los botones pueden configurarse para que aparezcan y se comporten como botones de opción, botones de radio o casillas. Normalmente, una barra de herramientas se alinea en la parte superior de una ventana de marco, pero una barra de herramientas de MFC puede "acoplarse" a cualquier lado de la ventana primaria o flotar en su propia ventana de marco reducido. Una barra de herramientas también puede "flotar" y puede cambiar su tamaño y arrastrarla con un mouse. Una barra de herramientas también puede mostrar información sobre herramientas cuando el usuario mueve el mouse sobre los botones de la barra de herramientas. Una información sobre herramientas es una pequeña ventana emergente que describe brevemente el propósito del botón.

> [!NOTE]
> A partir de la versión 4,0 de MFC, la clase [CToolBar](reference/ctoolbar-class.md) usa el control común de barra de herramientas de Windows. Un `CToolBar` contiene un [CToolBarCtrl](reference/ctoolbarctrl-class.md). Sin embargo, todavía se admiten las barras de herramientas anteriores. Vea las [barras de herramientas](mfc-toolbar-implementation.md)del artículo.

## <a name="status-bars"></a>Barras de estado

Una barra de estado es una barra de control que contiene paneles de salida de texto o "indicadores". Los paneles de salida se usan normalmente como líneas de mensaje y como indicadores de estado. Entre los ejemplos de línea de mensaje se incluyen la ayuda de comando-líneas de mensaje que explican brevemente el menú o el comando de barra de herramientas seleccionado en el panel izquierdo de la barra de estado predeterminada creada por el Asistente para aplicaciones MFC. Los ejemplos de indicadores de estado incluyen el bloqueo de desplazamiento, BLOQ NUM y otras claves. Las barras de Estado suelen estar alineadas en la parte inferior de una ventana de marco. Vea la clase [CStatusBar](reference/cstatusbar-class.md) y la clase [CStatusBarCtrl](reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Barras de cuadro de diálogo

Una barra de cuadro de diálogo es una barra de controles, basada en un recurso de plantilla de cuadro de diálogo, con la funcionalidad de un cuadro de diálogo no modal. Las barras de cuadro de diálogo pueden contener controles de Windows, personalizados o ActiveX. Como en un cuadro de diálogo, el usuario puede tabular entre los controles. Las barras de diálogo se pueden alinear en la parte superior, inferior, izquierda o derecha de una ventana de marco y también se pueden flotar en su propia ventana de marco. Vea la clase [CDialogBar](reference/cdialogbar-class.md).

## <a name="rebars"></a>Rebarras

Un [rebar](using-crebarctrl.md) es una barra de control que proporciona información de acoplamiento, diseño, estado y persistencia para los controles rebar. Un objeto rebar puede contener diversas ventanas secundarias, normalmente otros controles, como cuadros de edición, barras de herramientas y cuadros de lista. Un objeto rebar puede mostrar sus ventanas secundarias en un mapa de bits especificado. Se puede cambiar el tamaño de forma automática o manual haciendo clic o arrastrando su barra de redimensionamiento. Vea la clase [CReBar](reference/crebar-class.md).

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)

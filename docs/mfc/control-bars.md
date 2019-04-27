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
ms.openlocfilehash: 4b75d9a96f091d0424592f34bdb1ed7ce76c2372
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152788"
---
# <a name="control-bars"></a>Barras de controles

"Barra de control" es el nombre general para las barras de herramientas, barras de estado y las barras de cuadro de diálogo. Clases MFC `CToolBar`, `CStatusBar`, `CDialogBar`, `COleResizeBar`, y `CReBar` derivan de la clase [CControlBar](../mfc/reference/ccontrolbar-class.md), que implementa su funcionalidad habitual.

Barras de control son ventanas que muestran filas de controles con el que los usuarios pueden seleccionar opciones, ejecutar comandos u obtener información sobre el programa. Tipos de barras de control incluyen las barras de herramientas, barras de cuadro de diálogo y las barras de estado.

- Barras de herramientas, en la clase [CToolBar](../mfc/reference/ctoolbar-class.md)

- Barras de estado, en la clase [CStatusBar](../mfc/reference/cstatusbar-class.md)

- Barras de cuadro de diálogo, en la clase [CDialogBar](../mfc/reference/cdialogbar-class.md)

- Barras rebar, en la clase [CReBar](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
>  A partir de la versión 4.0 de MFC, las barras de herramientas, barras de estado y herramienta de sugerencias se implementan mediante la funcionalidad del sistema implementada en el *comctl32.dll* en lugar de la implementación anterior específica de MFC. En la versión 6.0, MFC `CReBar`, que también ajusta la funcionalidad de comctl32.dll, se ha agregado.

Siga el breve introducción a los tipos de la barra de control. Para obtener más información, consulte los vínculos siguientes.

## <a name="control-bars"></a>Barras de controles

Barras de control mejoran en gran medida la facilidad de uso de un programa proporcionando rápida, acciones de comando en un paso. Clase `CControlBar` proporciona la funcionalidad común de todas las barras de herramientas, barras de estado y las barras de cuadro de diálogo. `CControlBar` proporciona la funcionalidad para la colocación de la barra de control en su ventana de marco principal. Dado que una barra de controles es normalmente una ventana secundaria de una ventana de marco principal, es un "elemento relacionado" a la vista de cliente o el cliente MDI de la ventana de marco. Un objeto de barra de control usa información sobre el área rectangular de cliente de su ventana primaria para colocarse. A continuación, modifica restantes cliente rectángulo los padres para que la vista de cliente o la ventana de cliente MDI rellena el resto de la ventana del cliente.

> [!NOTE]
>  Si no tiene un botón en la barra de control una **comando** o **UPDATE_COMMAND_UI** controlador, el marco de trabajo deshabilita automáticamente el botón.

## <a name="toolbars"></a>Barras de herramientas

Una barra de herramientas es una barra de control que muestra una fila de botones de mapa de bits que llevar a cabo los comandos. Al presionar un botón de barra de herramientas equivale a elegir un elemento de menú; llama al mismo controlador asignado al elemento de menú si ese elemento de menú tiene el mismo identificador que el botón de barra de herramientas. Los botones pueden configurarse para que aparezcan y se comporten como botones de comando, los botones de radio o casillas de verificación. Una barra de herramientas normalmente se alinea a la parte superior de una ventana de marco, pero una barra de herramientas MFC puede "acoplar" a cualquier lado de su ventana primaria o float en su propia ventana de marco reducido. Una barra de herramientas también puede "flotar" y puede cambiar su tamaño y arrástrelo con el mouse. Una barra de herramientas también puede mostrar información sobre herramientas cuando el usuario mueve el mouse sobre los botones de la barra de herramientas. Una información sobre herramientas es una pequeña ventana emergente que se describe brevemente el propósito del botón.

> [!NOTE]
>  A partir de la versión 4.0 de MFC, clase [CToolBar](../mfc/reference/ctoolbar-class.md) usa el control común de barra de herramientas de Windows. Un `CToolBar` contiene un [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Sin embargo, las barras de herramientas anteriores todavía se admiten. Consulte el artículo [las barras de herramientas](../mfc/mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Barras de estado

Una barra de estado es una barra de control que contiene los paneles de salida de texto, o "indicadores". Los paneles de resultados se usan habitualmente como líneas de mensaje y como indicadores de estado. Algunos ejemplos de línea de mensaje son las líneas de comandos de mensaje de ayuda que explican brevemente el comando de barra de herramientas en el panel izquierdo de la barra de estado predeterminado creado por el Asistente para aplicaciones MFC o menú seleccionado. Ejemplos de indicador de estado incluyen otras claves, BLOQ NUM y Bloq Despl. Barras de estado normalmente se alinean en la parte inferior de una ventana de marco. Vea la clase [CStatusBar](../mfc/reference/cstatusbar-class.md) y clase [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Barras de cuadro de diálogo

Una barra de cuadro de diálogo es una barra de control, en función de un recurso de plantilla de cuadro de diálogo, con la funcionalidad de un cuadro de diálogo no modal. Las barras de cuadro de diálogo pueden contener Windows, personalizados o controles ActiveX. Como se muestra en un cuadro de diálogo, el usuario puede tabular entre los controles. Barras de cuadro de diálogo se pueden alinear a la parte superior, inferior, izquierda o derecha de una ventana de marco y también puede flotando en su propia ventana de marco. Vea la clase [CDialogBar](../mfc/reference/cdialogbar-class.md).

## <a name="rebars"></a>Barras rebar

Un [rebar](../mfc/using-crebarctrl.md) es una barra de control que proporciona información de acoplamiento, diseño, estado y la persistencia para controles rebar. Un objeto rebar puede contener una variedad de las ventanas secundarias, normalmente otros controles, incluidos los cuadros de edición, barras de herramientas y cuadros de lista. Un objeto rebar puede mostrar sus ventanas secundarias a través de un mapa de bits especificado. Se puede ser automática o manualmente cambiar su tamaño haciendo clic o arrastrando su barra de controles. Vea la clase [CReBar](../mfc/reference/crebar-class.md).

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)

---
title: Actualizar el texto de un panel de barra de estado
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: baf5013e34f262dd3bfed82941697ab9ca21e637
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280204"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Actualizar el texto de un panel de barra de estado

En este artículo se explica cómo cambiar el texto que aparece en un panel de barra de estado MFC. Una barra de estado, un objeto de clase de ventana [CStatusBar](../mfc/reference/cstatusbar-class.md) : contiene diversos "paneles". Cada panel es un área rectangular de la barra de estado que puede usar para mostrar información. Por ejemplo, muchas aplicaciones muestran el estado de las teclas BLOQ MAYÚS, BLOQ NUM y otras claves en los paneles más a la derecha. Las aplicaciones también suelen mostrar texto informativo en el panel izquierdo (panel 0), a veces denominado el "panel de mensajes". Por ejemplo, la barra de estado predeterminada MFC utiliza el panel de mensajes para mostrar una cadena que explica el botón de barra de herramientas o elemento de menú actualmente seleccionado. La figura [barras de estado](../mfc/status-bar-implementation-in-mfc.md) muestra una barra de estado de una aplicación MFC creada por el Asistente para la aplicación.

De forma predeterminada, MFC no se permite un `CStatusBar` panel cuando crea el panel. Para activar un panel, debe utilizar la macro ON_UPDATE_COMMAND_UI para cada panel en la barra de estado y actualizar los paneles. Dado que paneles no envían mensajes WM_COMMAND (no son como los botones de barra de herramientas), debe escribir el código manualmente.

Por ejemplo, suponga que tiene un panel `ID_INDICATOR_PAGE` como identificador de comando y que contiene el número de página actual en un documento. El siguiente procedimiento describe cómo crear un nuevo panel en la barra de estado.

### <a name="to-make-a-new-pane"></a>Para crear un panel nuevo

1. Definir el identificador de comando. del panel

   En el **vista** menú, haga clic en **vista de recursos**. Haga clic en el recurso de proyecto y haga clic en **símbolos de recursos**. En el cuadro de diálogo símbolos de recursos, haga clic en `New`. Escriba un nombre de identificador de comando: por ejemplo, `ID_INDICATOR_PAGE`. Especifique un valor para el identificador o acepte el valor sugerido por el cuadro de diálogo símbolos de recursos. Por ejemplo, para `ID_INDICATOR_PAGE`, acepte el valor predeterminado. Cierre el cuadro de diálogo símbolos de recursos.

1. Defina una cadena predeterminada para mostrar en el panel.

   Abra la vista de recursos, haga doble clic en **tabla de cadenas** en la ventana que se enumera los tipos de recursos para la aplicación. Con el **tabla de cadenas** editor abierto, elija **nueva cadena** desde el **insertar** menú. En la ventana Propiedades de cadena, seleccione el identificador del panel comando (por ejemplo, `ID_INDICATOR_PAGE`) y escriba un valor de cadena predeterminado, por ejemplo, "Página". Cierre el editor de cadenas. (Necesita una cadena predeterminada para evitar un error del compilador).

1. Agregar el panel a la *indicadores* matriz.

   En el archivo MAINFRM. CPP, busque el *indicadores* matriz. Esta matriz enumera los identificadores de comandos para todos los indicadores de la barra de estado, en orden de izquierda a derecha. En el punto adecuado de la matriz, escriba el identificador del panel comando, tal y como se muestra aquí para `ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

La manera recomendada de mostrar texto en un panel es llamar a la `SetText` función miembro de clase `CCmdUI` en una función de controlador de actualización para el panel. Por ejemplo, desea configurar una variable de entero *m_nPage* que contiene el número de página actual y la utilización `SetText` para establecer el texto del panel en una versión de cadena de ese número.

> [!NOTE]
>  El `SetText` enfoque se recomienda. Es posible llevar a cabo esta tarea en un nivel ligeramente inferior mediante una llamada a la `CStatusBar` función miembro `SetPaneText`. Aun así, todavía necesita un controlador de actualización. Sin un controlador para el panel, MFC deshabilita automáticamente el panel, borrar su contenido.

El procedimiento siguiente muestra cómo usar una función de controlador de actualización para mostrar texto en un panel.

#### <a name="to-make-a-pane-display-text"></a>Para hacer que un panel de mostrar texto

1. Agregar un controlador de actualización de comandos para el comando.

   Agregar manualmente un prototipo para el controlador, como se muestra aquí para `ID_INDICATOR_PAGE` (en MAINFRM. (H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. En el archivo. CPP, agregue la definición del controlador, como se muestra aquí para `ID_INDICATOR_PAGE` (en MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Las tres últimas líneas de este controlador son el código que muestra el texto.

1. En el mapa de mensajes apropiado, agregue la ON_UPDATE_COMMAND_UI (macro), como se muestra aquí para `ID_INDICATOR_PAGE` (en MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Una vez que defina el valor de la *m_nPage* variable miembro (de clase `CMainFrame`), esta técnica hace que el número de página aparecen en el panel durante el procesamiento en inactividad de la misma manera que la aplicación de actualizaciones de otros indicadores. Si *m_nPage* cambios, los cambios efectuados durante el siguiente bucle inactivo.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Actualizar objetos de interfaz de usuario (cómo actualizar los botones de barra de herramientas y elementos de menú como cambian las condiciones del programa)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Vea también

[Implementación de barra de estado en MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar (clase)](../mfc/reference/cstatusbar-class.md)

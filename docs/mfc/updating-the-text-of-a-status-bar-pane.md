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
ms.openlocfilehash: 20cd519f15fa9b218bca3dd1348659cfd0d5e473
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907637"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Actualizar el texto de un panel de barra de estado

En este artículo se explica cómo cambiar el texto que aparece en un panel de la barra de estado de MFC. Una barra de estado (un objeto de ventana de clase [CStatusBar](../mfc/reference/cstatusbar-class.md) ) contiene varios "paneles". Cada panel es un área rectangular de la barra de estado que puede usar para mostrar información. Por ejemplo, muchas aplicaciones muestran el estado de Bloq Mayús, BLOQ NUM y otras claves en los paneles situados más a la derecha. Las aplicaciones a menudo también muestran texto informativo en el panel izquierdo (panel 0), que a veces se denomina "panel de mensajes". Por ejemplo, la barra de estado predeterminada de MFC utiliza el panel de mensajes para mostrar una cadena que explica el elemento de menú o el botón de la barra de herramientas seleccionado actualmente. La figura de [barras de estado](../mfc/status-bar-implementation-in-mfc.md) muestra una barra de estado de una aplicación MFC creada por el Asistente para aplicaciones.

De forma predeterminada, MFC no habilita un `CStatusBar` panel cuando crea el panel. Para activar un panel, debe usar la macro ON_UPDATE_COMMAND_UI para cada panel de la barra de estado y actualizar los paneles. Dado que los paneles no envían mensajes WM_COMMAND (no son como los botones de la barra de herramientas), debe escribir el código manualmente.

Por ejemplo, suponga que un panel `ID_INDICATOR_PAGE` tiene como su identificador de comando y que contiene el número de página actual en un documento. En el procedimiento siguiente se describe cómo crear un nuevo panel en la barra de estado.

### <a name="to-make-a-new-pane"></a>Para crear un nuevo panel

1. Defina el identificador de comando del panel.

   En el menú **Ver** , haga clic en **vista de recursos**. Haga clic con el botón derecho en el recurso del proyecto y haga clic en **símbolos de recursos**. En el cuadro de diálogo símbolos de recursos `New`, haga clic en. Escriba un nombre de identificador de comando: por `ID_INDICATOR_PAGE`ejemplo,. Especifique un valor para el identificador o acepte el valor sugerido por el cuadro de diálogo símbolos de recursos. Por ejemplo, para `ID_INDICATOR_PAGE`, acepte el valor predeterminado. Cierre el cuadro de diálogo símbolos de recursos.

1. Defina una cadena predeterminada que se mostrará en el panel.

   Con Vista de recursos abierto, haga doble clic en **tabla de cadenas** en la ventana que muestra los tipos de recursos de la aplicación. Con el editor de **tabla de cadenas** abierto, elija **nueva cadena** en el menú **Insertar** . Seleccione el identificador de comando del panel (por ejemplo `ID_INDICATOR_PAGE`,) y escriba un valor de cadena predeterminado, como "página". Cierre el editor de cadenas. (Necesita una cadena predeterminada para evitar un error del compilador).

1. Agregue el panel a la matriz de *indicadores* .

   En archivo MAINFRM. CPP, busque la matriz de *indicadores* . Esta matriz muestra los identificadores de todos los indicadores de la barra de estado, en orden de izquierda a derecha. En el punto adecuado de la matriz, escriba el identificador de comando del panel, como se muestra `ID_INDICATOR_PAGE`aquí para:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

La manera recomendada de mostrar texto en un panel es llamar a la `SetText` función miembro de la `CCmdUI` clase en una función de controlador de actualización para el panel. Por ejemplo, puede que desee configurar una variable de entero *m_nPage* que contenga el número de página actual y utilizar `SetText` para establecer el texto del panel en una versión de cadena de ese número.

> [!NOTE]
>  Se `SetText` recomienda el enfoque. Es posible realizar esta tarea en un nivel ligeramente inferior llamando a la `CStatusBar` función `SetPaneText`miembro. Aun así, todavía necesita un controlador de actualización. Sin este tipo de controlador para el panel, MFC deshabilita automáticamente el panel, borrando su contenido.

En el procedimiento siguiente se muestra cómo utilizar una función de controlador de actualización para mostrar texto en un panel.

#### <a name="to-make-a-pane-display-text"></a>Para que un panel muestre texto

1. Agregue un controlador de actualización de comandos para el comando.

   Agregue manualmente un prototipo para el controlador, como se muestra aquí `ID_INDICATOR_PAGE` para (en MainFrm. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. En el adecuado. Archivo CPP, agregue la definición del controlador, como se muestra aquí `ID_INDICATOR_PAGE` para (en MainFrm. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Las tres últimas líneas de este controlador son el código que muestra el texto.

1. En el mapa de mensajes adecuado, agregue la macro ON_UPDATE_COMMAND_UI, como se muestra `ID_INDICATOR_PAGE` aquí para (en MainFrm. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Una vez que se define el valor de la variable miembro *m_nPage* ( `CMainFrame`de la clase), esta técnica hace que el número de página aparezca en el panel durante el procesamiento inactivo de la misma manera que la aplicación actualiza otros indicadores. Si *m_nPage* cambia, la pantalla cambia durante el siguiente bucle inactivo.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Actualizar objetos de la interfaz de usuario (cómo actualizar los botones de barra de herramientas y los elementos de menú a medida que las condiciones del programa cambian)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Vea también

[Implementación de barra de estado en MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar (clase)](../mfc/reference/cstatusbar-class.md)

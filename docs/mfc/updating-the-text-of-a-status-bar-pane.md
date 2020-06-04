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
ms.openlocfilehash: 723046fc1721cc46608e00f19a4431ef081be13d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366687"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Actualizar el texto de un panel de barra de estado

En este artículo se explica cómo cambiar el texto que aparece en un panel de la barra de estado MFC. Una barra de estado — un objeto de ventana de la clase [CStatusBar](../mfc/reference/cstatusbar-class.md) — contiene varios "panes." Cada panel es un área rectangular de la barra de estado que puede utilizar para mostrar información. Por ejemplo, muchas aplicaciones muestran el estado de las teclas BLOQUEO CAPS, BLOQUEO NUM y otras teclas en los paneles situados más a la derecha. Las aplicaciones también suelen mostrar texto informativo en el panel izquierdo (panel 0), a veces denominado "panel de mensajes." Por ejemplo, la barra de estado de MFC predeterminada utiliza el panel de mensajes para mostrar una cadena que explica el elemento de menú o el botón de barra de herramientas seleccionado actualmente. La figura de Barras de [estado](../mfc/status-bar-implementation-in-mfc.md) muestra una barra de estado de una aplicación MFC creada por el Asistente para aplicaciones.

De forma predeterminada, MFC `CStatusBar` no habilita un panel cuando crea el panel. Para activar un panel, debe usar la macro ON_UPDATE_COMMAND_UI para cada panel de la barra de estado y actualizar los paneles. Dado que los paneles no envían mensajes WM_COMMAND (no son como botones de barra de herramientas), debe escribir el código manualmente.

Por ejemplo, supongamos `ID_INDICATOR_PAGE` que un panel tiene como identificador de comando y que contiene el número de página actual en un documento. El siguiente procedimiento describe cómo crear un nuevo panel en la barra de estado.

### <a name="to-make-a-new-pane"></a>Para crear un nuevo panel

1. Defina el identificador de comando del panel.

   En el menú **Ver** , haga clic en **Vista de recursos**. Haga clic con el botón derecho en el recurso del proyecto y haga clic en **Símbolos de**recursos . En el cuadro de `New`diálogo Símbolos de recursos, haga clic en . Escriba un nombre de ID `ID_INDICATOR_PAGE`de comando: por ejemplo, . Especifique un valor para el identificador o acepte el valor sugerido por el cuadro de diálogo Símbolos de recursos. Por ejemplo, `ID_INDICATOR_PAGE`para , acepte el valor predeterminado. Cierre el cuadro de diálogo Símbolos de recursos.

1. Defina una cadena predeterminada para mostrar en el panel.

   Con la vista de recursos abierta, haga doble clic en **Tabla** de cadenas en la ventana que enumera los tipos de recursos de la aplicación. Con el editor **de tablas** de cadenas abierto, elija **Nueva cadena** en el menú **Insertar.** Seleccione el identificador de comando del `ID_INDICATOR_PAGE`panel (por ejemplo, ) y escriba un valor de cadena predeterminado, como "Página". Cierre el editor de cadenas. (Necesita una cadena predeterminada para evitar un error del compilador.)

1. Agregue el panel a la matriz *de indicadores.*

   En el archivo MAINFRM. CPP, localice la matriz de *indicadores.* Esta matriz enumera los guid de comando para todos los indicadores de la barra de estado, en orden de izquierda a derecha. En el punto apropiado de la matriz, ingrese el ID `ID_INDICATOR_PAGE`de comando del panel, como se muestra aquí para:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

La forma recomendada de mostrar texto en `SetText` un panel `CCmdUI` es llamar a la función miembro de la clase en una función de controlador de actualización para el panel. Por ejemplo, es posible que desee configurar una variable de `SetText` entero *m_nPage* que contenga el número de página actual y usar para establecer el texto del panel en una versión de cadena de ese número.

> [!NOTE]
> Se `SetText` recomienda el enfoque. Es posible realizar esta tarea en un nivel `CStatusBar` ligeramente inferior llamando a la función `SetPaneText`miembro . Aún así, todavía necesita un controlador de actualización. Sin este controlador para el panel, MFC deshabilita automáticamente el panel, borrando su contenido.

El siguiente procedimiento muestra cómo utilizar una función de controlador de actualización para mostrar texto en un panel.

#### <a name="to-make-a-pane-display-text"></a>Para hacer que un panel muestre texto

1. Agregue un controlador de actualización de comandos para el comando.

   Agregue manualmente un prototipo para el controlador, como se muestra aquí para `ID_INDICATOR_PAGE` (en MAINFRM. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. En el archivo . CPP, agregue la definición del controlador, `ID_INDICATOR_PAGE` como se muestra aquí para (en MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Las tres últimas líneas de este controlador son el código que muestra el texto.

1. En el mapa de mensajes adecuado, agregue `ID_INDICATOR_PAGE` la macro ON_UPDATE_COMMAND_UI, como se muestra aquí para (en MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Una vez definido el valor de la `CMainFrame`variable miembro *m_nPage* (de clase), esta técnica hace que el número de página aparezca en el panel durante el procesamiento inactivo de la misma manera que la aplicación actualiza otros indicadores. Si *m_nPage* cambia, la visualización cambia durante el siguiente bucle inactivo.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Actualización de objetos de interfaz de usuario (cómo actualizar los botones de la barra de herramientas y los elementos de menú a medida que cambian las condiciones del programa)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Consulte también

[Implementación de barra de estado en MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[Clase CStatusBar](../mfc/reference/cstatusbar-class.md)

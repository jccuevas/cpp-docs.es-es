---
title: Actualizar el texto de un panel de barra de estado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbb2f14f274be3c7282a897c271049fe46434f3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384483"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Actualizar el texto de un panel de barra de estado
En este artículo se explica cómo cambiar el texto que aparece en un panel de barra de estado MFC. Una barra de estado, un objeto de ventana de clase [CStatusBar](../mfc/reference/cstatusbar-class.md) : contiene varios "paneles". Cada panel es un área rectangular de la barra de estado que se puede usar para mostrar información. Por ejemplo, muchas aplicaciones mostrar el estado de las teclas BLOQ MAYÚS, BLOQ NUM y otras claves en los paneles más a la derecha. Las aplicaciones también suelen mostrar texto informativo en el panel izquierdo (panel 0), a veces denominado el "panel de mensajes". Por ejemplo, la barra de estado MFC predeterminada usa el panel de mensajes para mostrar una cadena que explica el botón de barra de herramientas o elemento de menú actualmente seleccionado. En la ilustración en [barras de estado](../mfc/status-bar-implementation-in-mfc.md) muestra una barra de estado de una aplicación creada por el Asistente para aplicaciones MFC.  
  
 De forma predeterminada, MFC no permite un `CStatusBar` panel al crear el panel. Para activar un panel, debe utilizar el `ON_UPDATE_COMMAND_UI` macro para cada panel en el estado de la barra y actualizar los paneles. Ya no se envían paneles **WM_COMMAND** mensajes (no como botones de barra de herramientas), debe escribir el código manualmente.  
  
 Por ejemplo, imagine que tiene un panel `ID_INDICATOR_PAGE` como su identificador de comando y que contiene el número de página actual en un documento. El siguiente procedimiento describe cómo crear un nuevo panel en la barra de estado.  
  
### <a name="to-make-a-new-pane"></a>Para crear un panel nuevo  
  
1.  Definir el identificador del comando. del panel  
  
     En el **vista** menú, haga clic en **vista de recursos**. Haga clic en el recurso del proyecto y haga clic en **símbolos de recursos**. En el cuadro de diálogo símbolos de recursos, haga clic en `New`. Escriba un nombre de Id. de comando: por ejemplo, `ID_INDICATOR_PAGE`. Especificar un valor para el identificador o acepte el valor sugerido en el cuadro de diálogo símbolos de recursos. Por ejemplo, para `ID_INDICATOR_PAGE`, acepte el valor predeterminado. Cierre el cuadro de diálogo símbolos de recursos.  
  
2.  Defina una cadena predeterminada para mostrar en el panel.  
  
     Con la vista de recursos abierta, haga doble clic en **tabla de cadenas** en la ventana que enumera los tipos de recursos para la aplicación. Con el **tabla de cadenas** editor abierto, elija **nueva cadena** desde el **insertar** menú. En la ventana Propiedades de cadena, seleccione el identificador del panel comando (por ejemplo, `ID_INDICATOR_PAGE`) y escriba un valor de cadena predeterminado, como "Página". Cierre el editor de cadenas. (Se necesita una cadena predeterminada para evitar un error del compilador).  
  
3.  Agregar el panel a la **indicadores** matriz.  
  
     En el archivo MAINFRM. CPP, busque el **indicadores** matriz. Esta matriz enumera los identificadores de comando para todos los indicadores de la barra de estado, en orden, de izquierda a derecha. En el punto adecuado de la matriz, escriba el identificador del panel comando, como se muestra aquí para `ID_INDICATOR_PAGE`:  
  
     [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]  
  
 La manera recomendada de mostrar texto en un panel es llamar a la **SetText** función miembro de clase `CCmdUI` en una función de controlador de actualización para el panel. Por ejemplo, puede configurar una variable de entero `m_nPage` que contiene el número de página actual y el uso **SetText** para establecer el texto del panel a una versión de cadena de ese número.  
  
> [!NOTE]
>  El **SetText** opción es recomendable. Es posible realizar esta tarea en un nivel ligeramente inferior mediante una llamada a la `CStatusBar` función miembro `SetPaneText`. Aun así, todavía necesita un controlador de actualización. Sin este tipo de controlador para el panel, MFC deshabilita automáticamente el panel, borrar su contenido.  
  
 El siguiente procedimiento muestra cómo utilizar una función de controlador de actualización para mostrar texto en un panel.  
  
#### <a name="to-make-a-pane-display-text"></a>Para hacer que un panel muestre texto  
  
1.  Agregue un controlador de actualización de comandos para el comando.  
  
     Agregar manualmente un prototipo para el controlador, como se muestra aquí para `ID_INDICATOR_PAGE` (en MAINFRM. (H):  
  
     [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]  
  
2.  En el archivo. CPP Archivo, agregue la definición del controlador, como se muestra aquí para `ID_INDICATOR_PAGE` (en MAINFRM. CPP):  
  
     [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]  
  
     Las tres últimas líneas de este controlador son el código que muestra el texto.  
  
3.  En el mapa de mensajes apropiado, agregue el `ON_UPDATE_COMMAND_UI` macro, tal y como se muestra aquí para `ID_INDICATOR_PAGE` (en MAINFRM. CPP):  
  
     [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]  
  
 Una vez que defina el valor de la `m_nPage` variable miembro (de clase `CMainFrame`), esta técnica hace que el número de página para que aparezcan en el panel durante el procesamiento en inactividad de la misma manera que la aplicación actualiza otros indicadores. Si `m_nPage` cambios, los cambios efectuados durante el siguiente bucle inactivo.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Actualizar objetos de la interfaz de usuario (cómo actualizar botones de barra de herramientas y los elementos de menú que cambian las condiciones del programa)](../mfc/how-to-update-user-interface-objects.md)  
  
## <a name="see-also"></a>Vea también  
 [Implementación de la barra de estado en MFC](../mfc/status-bar-implementation-in-mfc.md)   
 [CStatusBar (clase)](../mfc/reference/cstatusbar-class.md)

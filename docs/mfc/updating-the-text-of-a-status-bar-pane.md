---
title: "Actualizar el texto de un panel de barra de estado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBar (clase), actualizar"
  - "ON_UPDATE_COMMAND_UI (macro)"
  - "paneles, barra de estado"
  - "SetText (método)"
  - "barras de estado, actualizar"
  - "texto, barra de estado"
  - "actualizar objetos de la interfaz de usuario"
  - "objetos de interfaz de usuario, actualizar"
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Actualizar el texto de un panel de barra de estado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo cambiar el texto que aparece en un panel de barra de estado de MFC.  Una barra de estado — un objeto en la ventana de la clase [CStatusBar](../mfc/reference/cstatusbar-class.md) contiene varios “paneles”. Cada panel es un área rectangular de la barra de estado que se puede utilizar para mostrar información.  Por ejemplo, muchas aplicaciones muestran el estado de BLOQ MAYÚS, de BLOQ NUM, y otras claves en los paneles de derecha.  Las aplicaciones también muestran a menudo texto informativo en el panel de la izquierda \(panel 0\), a veces denominado “panel de mensajes”. Por ejemplo, la barra de estado de MFC predeterminado utiliza el panel de mensajes para mostrar una cadena que explica el elemento de menú o el botón de la barra de herramientas actualmente seleccionado.  La ilustración de [Barras de estado](../mfc/status-bar-implementation-in-mfc.md) muestra una barra de estado de una aplicación MFC Asistente\- creada aplicación.  
  
 De forma predeterminada, MFC no permite un panel de `CStatusBar` cuando crea el panel.  Para activar un panel, debe utilizar la macro de `ON_UPDATE_COMMAND_UI` para cada panel en la barra de estado y actualizar los paneles.  Dado que los paneles no envían mensajes de **WM\_COMMAND** \(no son como los botones de la barra de herramientas\), debe escribir el código manualmente.  
  
 Por ejemplo, suponga que un panel tiene `ID_INDICATOR_PAGE` como identificador de comandos y que contiene el número de página actual en un documento.  El procedimiento siguiente describe cómo crear un nuevo panel en la barra de estado.  
  
### Para crear un nuevo panel  
  
1.  Defina la identificación del panel  
  
     En el menú de **Visualización** , haga clic en **vista de recursos**.  Haga clic con el botón secundario en el recurso y haga clic en **Símbolos de recursos**del proyecto.  En el cuadro de diálogo símbolos de recursos, haga clic en `New`.  Escriba un nombre de identificador de comando: por ejemplo, `ID_INDICATOR_PAGE`.  Especifique un valor para el identificador, o acepte el valor sugerido por el cuadro de diálogo símbolos de recursos.  Por ejemplo, para `ID_INDICATOR_PAGE`, acepte el valor predeterminado.  Cierre el cuadro de diálogo símbolos de recursos.  
  
2.  Defina una cadena predeterminada que se muestra en el panel.  
  
     Con la vista de recursos abierto, haga doble clic en **Tabla de cadenas** en la ventana que muestra los tipos de recursos para la aplicación.  Con el editor de **Tabla de cadenas** abiertos, elija **Nueva cadena** de menú de **INSERT** .  En la ventana Propiedades de la cadena, seleccione el identificador de comando del panel \(por ejemplo, `ID_INDICATOR_PAGE`\) y escriba un valor de cadena predeterminado, como “página”.  Cierre el editor de cadenas. \(Necesita una cadena predeterminada evitar un error del compilador.\)  
  
3.  Agregue el panel a la matriz de **indicators** .  
  
     En el archivo MAINFRM.CPP, busque la matriz de **indicators** .  Id. de este de matriz comando de listas para los todos los indicadores de barra de estado, ordenados de izquierda a derecha.  En el punto adecuado en la matriz, escriba el identificador de comando del panel, como se muestra aquí para `ID_INDICATOR_PAGE`:  
  
     [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_1.cpp)]  
  
 La manera recomendada de mostrar texto en un panel es llamar a la función miembro de **SetText** de la clase `CCmdUI` en una función de controlador de actualización para el panel.  Por ejemplo, puede configurar una variable integer `m_nPage` que contiene el número de página actual y el uso **SetText** de establecer el texto del panel a una versión de cadena de ese número.  
  
> [!NOTE]
>  Se recomienda el enfoque de **SetText** .  Es posible realizar esta tarea en un ligeramente de nivel inferior llamando a la función `SetPaneText`miembro de `CStatusBar` .  Sin embargo, todavía necesita actualizar el controlador.  Sin estos controladores para el panel, MFC automáticamente deshabilita el panel, borrando su contenido.  
  
 El siguiente procedimiento muestra cómo utilizar una función de controlador de actualización para mostrar texto en un panel.  
  
#### Para que un panel muestra el texto  
  
1.  Agregue un controlador de actualización de comandos para el comando.  
  
     Agregue manualmente un prototipo del controlador, como se muestra aquí para `ID_INDICATOR_PAGE` \(en MAINFRM.H\):  
  
     [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_2.h)]  
  
2.  En el archivo adecuado de .CPP, agregue la definición del controlador, como se muestra aquí para `ID_INDICATOR_PAGE` \(en MAINFRM.CPP\):  
  
     [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_3.cpp)]  
  
     Las tres líneas pasadas de este controlador son el código que muestra el texto.  
  
3.  En el mapa del mensaje, agregue la macro de `ON_UPDATE_COMMAND_UI` , como se muestra aquí para `ID_INDICATOR_PAGE` \(en MAINFRM.CPP\):  
  
     [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_4.cpp)]  
  
 Una vez que se define el valor de la variable miembro de `m_nPage` \(de la clase `CMainFrame`\), las causas de esta técnica el número de página de aparecer en el panel durante el procesamiento inactivo de la misma manera que la aplicación actualiza otros marcadores.  Si cambia de `m_nPage` , la pantalla durante el bucle inactivo siguiente.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Actualizar objetos de la interfaz de usuario \(cómo actualizar los botones de la barra de herramientas y elementos de menú como cambio de las condiciones de programa\)](../mfc/how-to-update-user-interface-objects.md)  
  
## Vea también  
 [Implementación de barra de estado en MFC](../mfc/status-bar-implementation-in-mfc.md)   
 [CStatusBar Class](../mfc/reference/cstatusbar-class.md)
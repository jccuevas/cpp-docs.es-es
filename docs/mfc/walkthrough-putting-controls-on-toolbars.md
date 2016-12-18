---
title: "Tutorial: Poner controles en las barras de herramientas | Microsoft Docs"
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
  - "Personalizar (cuadro de diálogo), agregar controles"
  - "barras de herramientas, agregar controles"
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Poner controles en las barras de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se describe cómo agregar a una barra de herramientas un botón de barra de herramientas que contiene un control de Windows.  En MFC, un botón de barra de herramientas debe ser una clase derivada de [CMFCToolBarButton Class](../mfc/reference/cmfctoolbarbutton-class.md), por ejemplo [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton Class](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton Class](../mfc/reference/cmfcdropdowntoolbarbutton-class.md) o [CMFCToolBarMenuButton Class](../mfc/reference/cmfctoolbarmenubutton-class.md).  
  
## Agregar controles a barras de herramientas  
 Para agregar un control a una barra de herramientas, siga estos pasos:  
  
1.  Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.  Para obtener más información sobre cómo crear botones mediante el editor de barras de herramientas de Visual Studio, vea el tema [Toolbar Editor](../mfc/toolbar-editor.md).  
  
2.  Reserve una imagen de la barra de herramientas \(icono de botón\) para el botón en todos los mapas de bits de la barra de herramientas principal.  
  
3.  En el controlador de mensajes que procesa el mensaje `AFX_WM_RESETTOOLBAR`, haga lo siguiente:  
  
    1.  Crear el control de botón mediante una clase derivada de `CMFCToolbarButton`.  
  
    2.  Reemplace el botón ficticio por el nuevo control mediante [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md).  Puede crear el objeto del botón en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.  
  
> [!NOTE]
>  Si ha habilitado la personalización en la aplicación, quizás tenga que restablecer la barra de herramientas mediante el botón **Restablecer** en la pestaña **Barras de herramientas** del cuadro de diálogo **Personalizar** para ver el control actualizado en la aplicación después de volver a compilar.  El estado de la barra de herramientas se guarda en el Registro de Windows y la información del Registro se carga y se aplica después de que el método `ReplaceButton` se ejecute durante el inicio de la aplicación.  
  
## Controles de barra de herramientas y personalización  
 La pestaña **Comandos** del cuadro de diálogo **Personalizar** contiene una lista de comandos que está disponible en la aplicación.  De forma predeterminada, el cuadro de diálogo **Personalizar** procesa los menús de la aplicación y compila una lista de botones de barra de herramientas estándar en cada categoría de menú.  Para conservar la funcionalidad extendida que los controles de barra de herramientas proporcionan, debe reemplazar el botón de barra de herramientas estándar por el control personalizado en el cuadro de diálogo **Personalizar**.  
  
 Al habilitar la personalización, se crea el cuadro de diálogo **Personalizar** en el controlador de personalización `OnViewCustomize` mediante la clase [CMFCToolBarsCustomizeDialog Class](../mfc/reference/cmfctoolbarscustomizedialog-class.md).  Antes de mostrar el cuadro de diálogo **Personalizar** llamando a [CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md), llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md) para reemplazar el botón estándar por el nuevo.  
  
## Ejemplo: Crear un cuadro combinado de búsqueda  
 En esta sección se describe cómo crear un control de cuadro combinado `Find` que aparece en una barra de herramientas y contiene las cadenas de búsqueda usadas recientemente.  El usuario puede escribir una cadena en el control y, después, presionar la tecla Entrar para buscar un documento o presionar la tecla Escape para devolver el foco al marco principal.  En este ejemplo se supone que el documento aparece en una vista derivada de [CEditView Class](../mfc/reference/ceditview-class.md).  
  
### Crear el control Buscar  
 Primero, cree el control de cuadro combinado `Find`:  
  
1.  Agregue el botón y los comandos a los recursos de la aplicación:  
  
    1.  En los recursos de la aplicación, agregue un nuevo botón con un id. de comando `ID_EDIT_FIND` a una barra de herramientas de la aplicación y a los mapas de bits asociados a la barra de herramientas.  
  
    2.  Cree un nuevo elemento de menú con el id. de comando ID\_EDIT\_FIND.  
  
    3.  Agregue una nueva cadena "Buscar el texto\\nBuscar" a la tabla de cadenas y asígnele un id. de comando `ID_EDIT_FIND_COMBO`.  Este identificador se utilizará como id. de comando del botón de cuadro combinado `Find`.  
  
        > [!NOTE]
        >  Dado que `ID_EDIT_FIND` es un comando estándar que se procesa mediante `CEditView`, no es necesario implementar un controlador especial para este comando.  Sin embargo, debe implementar un controlador para el nuevo comando `ID_EDIT_FIND_COMBO`.  
  
2.  Cree una nueva clase, `CFindComboBox`, derivada de [CComboBox Class](../mfc/reference/ccombobox-class.md).  
  
3.  En la clase `CFindComboBox`, invalide el método virtual `PreTranslateMessage`.  Este método habilitará el cuadro combinado para procesar el mensaje de [WM\_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280).  Si el usuario presiona la tecla Escape \(`VK_ESCAPE`\), devuelve el foco a la ventana marco principal.  Si el usuario presiona la tecla Entrar \(`VK_ENTER`\), envía a la ventana marco principal un mensaje de `WM_COMMAND` que contiene el id. de comando `ID_EDIT_FIND_COMBO`.  
  
4.  Cree una clase para el botón de cuadro combinado `Find`, derivado de [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md).  En este ejemplo, se denomina `CFindComboButton`.  
  
5.  El constructor de `CMFCToolbarComboBoxButton` toma tres parámetros: el id. de comando del botón, el índice de la imagen del botón y el estilo del cuadro combinado.  Establezca estos parámetros de la siguiente forma:  
  
    1.  Pase `ID_EDIT_FIND_COMBO` como el id. de comando.  
  
    2.  Utilice [CCommandManager::GetCmdImage](http://msdn.microsoft.com/es-es/4094d08e-de74-4398-a483-76d27a742dca) con `ID_EDIT_FIND` para obtener el índice de la imagen.  
  
    3.  Para obtener una lista de los estilos de cuadro combinado disponibles, vea [Estilos de cuadro combinado](../mfc/reference/combo-box-styles.md).  
  
6.  En la clase `CFindComboButton`, invalide el método `CMFCToolbarComboBoxButton::CreateCombo`.  Aquí se debe crear el objeto `CFindComboButton` y devolver un puntero a él.  
  
7.  Utilice la macro [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) para hacer que el botón combinado sea persistente.  El administrador del área de trabajo carga y guarda automáticamente el estado del botón en el Registro de Windows.  
  
8.  Implemente el controlador `ID_EDIT_FIND_COMBO` en la vista del documento.  Utilice [CMFCToolBar::GetCommandButtons](../Topic/CMFCToolBar::GetCommandButtons.md) con `ID_EDIT_FIND_COMBO` para recuperar todos los botones de cuadro combinado `Find`.  Puede haber varias copias de un botón con el mismo id. de comando debido a la personalización.  
  
9. En el controlador de mensajes `OnFind` de ID\_EDIT\_FIND, utilice [CMFCToolBar::IsLastCommandFromButton](../Topic/CMFCToolBar::IsLastCommandFromButton.md) para determinar si se ha enviado el comando Buscar desde el botón de cuadro combinado `Find`.  Si es así, busque el texto y agregue la cadena de búsqueda al cuadro combinado.  
  
### Agregar el control Buscar a la barra de herramientas principal  
 Para agregar el botón de cuadro combinado a la barra de herramientas, siga estos pasos:  
  
1.  Implemente el controlador de mensajes `OnToolbarReset` de `AFX_WM_RESETTOOLBAR` en la ventana marco principal.  
  
    > [!NOTE]
    >  El marco envía este mensaje a la ventana marco principal cuando se inicializa una barra de herramientas durante el inicio de la aplicación o cuando se restaura una barra de herramientas durante la personalización.  En cualquier caso, debe reemplazar el botón de barra de herramientas estándar por el botón del cuadro combinado `Find` personalizado.  
  
2.  En el controlador `AFX_WM_RESETTOOLBAR`, examine el id. de barra de herramientas, es decir, `WPARAM` del mensaje `AFX_WM_RESETTOOLBAR`.  Si el id. de barra de herramientas es igual al de la barra de herramientas que contiene el botón de cuadro combinado `Find`, llame a [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md) para reemplazar el botón `Find` \(es decir, el botón con el id. de comando `ID_EDIT_FIND)` por un objeto `CFindComboButton`.  
  
    > [!NOTE]
    >  Puede crear un objeto `CFindComboBox` en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.  
  
### Agregar el control Buscar al cuadro de diálogo Personalizar  
 En el controlador de personalización `OnViewCustomize`, llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md) para reemplazar el botón `Find` \(es decir, el botón con el id. de comando `ID_EDIT_FIND)` por un objeto `CFindComboButton`.  
  
## Vea también  
 [Gráfico de jerarquías](../mfc/hierarchy-chart.md)   
 [Clases](../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog Class](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
---
title: 'Tutorial: Poner controles en barras de herramientas | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f991f8ebf87535de09dc7c3dce5e0f4ca2ee457b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Tutorial: Poner controles en las barras de herramientas
En este tema se describe cómo agregar a una barra de herramientas un botón de barra de herramientas que contiene un control de Windows. En MFC, un botón de barra de herramientas debe ser un [CMFCToolBarButton clase](../mfc/reference/cmfctoolbarbutton-class.md)-clase derivada, por ejemplo [CMFCToolBarComboBoxButton clase](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton clase](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton clase](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), o [CMFCToolBarMenuButton clase](../mfc/reference/cmfctoolbarmenubutton-class.md).  
  
## <a name="adding-controls-to-toolbars"></a>Agregar controles a barras de herramientas  
 Para agregar un control a una barra de herramientas, siga estos pasos:  
  
1.  Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas. Para obtener más información sobre cómo crear botones mediante el Editor de la barra de herramientas en Visual Studio, consulte el [barra de herramientas del Editor](../windows/toolbar-editor.md) tema.  
  
2.  Reserve una imagen de la barra de herramientas (icono de botón) para el botón en todos los mapas de bits de la barra de herramientas principal.  
  
3.  En el controlador de mensajes que procesa el mensaje `AFX_WM_RESETTOOLBAR`, haga lo siguiente:  
  
    1.  Crear el control de botón mediante una clase derivada de `CMFCToolbarButton`.  
  
    2.  Reemplazar el botón ficticio con el nuevo control mediante [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Puede crear el objeto del botón en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.  
  
> [!NOTE]
>  Si ha habilitado la personalización de la aplicación, tendrá que restablecer la barra de herramientas mediante el **restablecer** situado en la **las barras de herramientas** pestaña de la **personalizar** cuadro de diálogo para ver el control actualizado en la aplicación después de volver a compilar. El estado de la barra de herramientas se guarda en el Registro de Windows y la información del Registro se carga y se aplica después de que el método `ReplaceButton` se ejecute durante el inicio de la aplicación.  
  
## <a name="toolbar-controls-and-customization"></a>Controles de barra de herramientas y personalización  
 El **comandos** pestaña de la **personalizar** cuadro de diálogo contiene una lista de comandos que están disponibles en la aplicación. De forma predeterminada, el **personalizar** cuadro de diálogo procesa los menús de la aplicación y compila una lista de botones de barra de herramientas estándar en cada categoría de menú. Para conservar la funcionalidad extendida que proporcionan los controles de barra de herramientas, debe reemplazar el botón de barra de herramientas estándar con el control personalizado en el **personalizar** cuadro de diálogo.  
  
 Cuando se habilita la personalización, crear el **personalizar** cuadro de diálogo en el controlador de personalización `OnViewCustomize` mediante el uso de la [CMFCToolBarsCustomizeDialog clase](../mfc/reference/cmfctoolbarscustomizedialog-class.md) clase. Antes de mostrar la **personalizar** cuadro de diálogo mediante una llamada a [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar el botón estándar con el nuevo control.  
  
## <a name="example-creating-a-find-combo-box"></a>Ejemplo: Crear un cuadro combinado de búsqueda  
 En esta sección se describe cómo crear un control de cuadro combinado `Find` que aparece en una barra de herramientas y contiene las cadenas de búsqueda usadas recientemente. El usuario puede escribir una cadena en el control y, después, presionar la tecla Entrar para buscar un documento o presionar la tecla Escape para devolver el foco al marco principal. En este ejemplo se da por supuesto que el documento se muestra en un [clase CEditView](../mfc/reference/ceditview-class.md)-derivados de la vista.  
  
### <a name="creating-the-find-control"></a>Crear el control Buscar  
 Primero, cree el control de cuadro combinado `Find`:  
  
1.  Agregue el botón y los comandos a los recursos de la aplicación:  
  
    1.  En los recursos de la aplicación, agregue un nuevo botón con un id. de comando `ID_EDIT_FIND` a una barra de herramientas de la aplicación y a los mapas de bits asociados a la barra de herramientas.  
  
    2.  Cree un nuevo elemento de menú con el id. de comando ID_EDIT_FIND.  
  
    3.  Agregue una nueva cadena "Buscar el texto\nBuscar" a la tabla de cadenas y asígnele un id. de comando `ID_EDIT_FIND_COMBO`. Este identificador se utilizará como id. de comando del botón de cuadro combinado `Find`.  
  
        > [!NOTE]
        >  Dado que `ID_EDIT_FIND` es un comando estándar que se procesa mediante `CEditView`, no es necesario implementar un controlador especial para este comando.  Sin embargo, debe implementar un controlador para el nuevo comando `ID_EDIT_FIND_COMBO`.  
  
2.  Cree una nueva clase, `CFindComboBox`, derivado del [CComboBox (clase)](../mfc/reference/ccombobox-class.md).  
  
3.  En la clase `CFindComboBox`, invalide el método virtual `PreTranslateMessage`. Este método habilitará el cuadro combinado para procesar el [WM_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) mensaje. Si el usuario presiona la tecla Escape (`VK_ESCAPE`), devuelve el foco a la ventana marco principal. Si el usuario presiona la tecla Entrar (`VK_ENTER`), envía a la ventana marco principal un mensaje de `WM_COMMAND` que contiene el id. de comando `ID_EDIT_FIND_COMBO`.  
  
4.  Cree una clase para la `Find` botón del cuadro combinado, derivado de [CMFCToolBarComboBoxButton clase](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). En este ejemplo, se denomina `CFindComboButton`.  
  
5.  El constructor de `CMFCToolbarComboBoxButton` toma tres parámetros: el id. de comando del botón, el índice de la imagen del botón y el estilo del cuadro combinado. Establezca estos parámetros de la siguiente forma:  
  
    1.  Pase `ID_EDIT_FIND_COMBO` como el id. de comando.  
  
    2.  Use [CCommandManager::GetCmdImage](http://msdn.microsoft.com/en-us/4094d08e-de74-4398-a483-76d27a742dca) con `ID_EDIT_FIND` para obtener el índice de imagen.  
  
    3.  Para obtener una lista de estilos de cuadro combinado, vea [estilos de cuadro combinado](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
6.  En la clase `CFindComboButton`, invalide el método `CMFCToolbarComboBoxButton::CreateCombo`. Aquí se debe crear el objeto `CFindComboButton` y devolver un puntero a él.  
  
7.  Use la [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) macro para hacer persistente el botón combinado. El administrador del área de trabajo carga y guarda automáticamente el estado del botón en el Registro de Windows.  
  
8.  Implemente el controlador `ID_EDIT_FIND_COMBO` en la vista del documento. Use [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) con `ID_EDIT_FIND_COMBO` para recuperar todos `Find` botones del cuadro combinado. Puede haber varias copias de un botón con el mismo id. de comando debido a la personalización.  
  
9. En el controlador de mensajes ID_EDIT_FIND `OnFind`, use [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) para determinar si el comando find fue enviado desde el `Find` botón del cuadro combinado. Si es así, busque el texto y agregue la cadena de búsqueda al cuadro combinado.  
  
### <a name="adding-the-find-control-to-the-main-toolbar"></a>Agregar el control Buscar a la barra de herramientas principal  
 Para agregar el botón de cuadro combinado a la barra de herramientas, siga estos pasos:  
  
1.  Implemente el controlador de mensajes `AFX_WM_RESETTOOLBAR` de `OnToolbarReset` en la ventana marco principal.  
  
    > [!NOTE]
    >  El marco envía este mensaje a la ventana marco principal cuando se inicializa una barra de herramientas durante el inicio de la aplicación o cuando se restaura una barra de herramientas durante la personalización. En cualquier caso, debe reemplazar el botón de barra de herramientas estándar por el botón del cuadro combinado `Find` personalizado.  
  
2.  En el controlador `AFX_WM_RESETTOOLBAR`, examine el id. de barra de herramientas, es decir, `WPARAM` del mensaje `AFX_WM_RESETTOOLBAR`. Si el identificador de la barra de herramientas es igual al de la barra de herramientas que contiene el `Find` botón del cuadro combinado, llamada [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) para reemplazar el `Find` botón (es decir, el botón con el identificador de comando `ID_EDIT_FIND)` con un `CFindComboButton` objeto.  
  
    > [!NOTE]
    >  Puede crear un objeto `CFindComboBox` en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.  
  
### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Agregar el control Buscar al cuadro de diálogo Personalizar  
 En el controlador de personalización `OnViewCustomize`, llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar el `Find` botón (es decir, el botón con el identificador de comando `ID_EDIT_FIND)` con un `CFindComboButton` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../mfc/hierarchy-chart.md)   
 [Clases](../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)   
 [Clase CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog (clase)](../mfc/reference/cmfctoolbarscustomizedialog-class.md)

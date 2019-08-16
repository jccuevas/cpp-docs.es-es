---
title: 'Tutorial: Colocar controles en las barras de herramientas'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 0c62a8b484cb666427f873244221afec5d4719da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510740"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Tutorial: Colocar controles en las barras de herramientas

En este artículo se describe cómo agregar un botón de la barra de herramientas que contiene un control de Windows a una barra de herramientas. En MFC, un botón de barra de herramientas debe ser una clase derivada de la [clase CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md), por ejemplo, clase [CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), clase [CMFCToolBarEditBoxButton](../mfc/reference/cmfctoolbareditboxbutton-class.md), clase [CMFCDropDownToolbarButton](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)o [ Clase CMFCToolBarMenuButton](../mfc/reference/cmfctoolbarmenubutton-class.md).

## <a name="adding-controls-to-toolbars"></a>Agregar controles a barras de herramientas

Para agregar un control a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas. Para obtener más información sobre cómo crear botones mediante el editor de la **barra de herramientas** de Visual Studio, vea el artículo editor de la [barra de herramientas](../windows/toolbar-editor.md) .

1. Reserve una imagen de la barra de herramientas (icono de botón) para el botón en todos los mapas de bits de la barra de herramientas principal.

1. En el controlador de mensajes que procesa `AFX_WM_RESETTOOLBAR` el mensaje, siga estos pasos:

   1. Crear el control de botón mediante una clase derivada de `CMFCToolbarButton`.

   1. Reemplace el botón ficticio por el nuevo control mediante [CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Puede crear el objeto del botón en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.

> [!NOTE]
>  Si ha habilitado la personalización en la aplicación, es posible que tenga que restablecer la barra de herramientas mediante el botón **restablecer** de la pestaña **barras de herramientas** del cuadro de diálogo **personalizar** para ver el control actualizado en la aplicación después de volver a compilar. El estado de la barra de herramientas se guarda en el Registro de Windows y la información del Registro se carga y se aplica después de que el método `ReplaceButton` se ejecute durante el inicio de la aplicación.

## <a name="toolbar-controls-and-customization"></a>Controles de barra de herramientas y personalización

La pestaña **comandos** del cuadro de diálogo **personalizar** contiene una lista de comandos que están disponibles en la aplicación. De forma predeterminada, el cuadro de diálogo **personalizar** procesa los menús de la aplicación y genera una lista de botones de la barra de herramientas estándar en cada categoría del menú. Para mantener la funcionalidad extendida que proporcionan los controles de barra de herramientas, debe reemplazar el botón de la barra de herramientas estándar por el control personalizado en el cuadro de diálogo **personalizar** .

Al habilitar la personalización, se crea el cuadro de diálogo **personalizar** en el controlador `OnViewCustomize` de personalización mediante la clase de [clase CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md) . Antes de mostrar el cuadro de diálogo **personalizar** llamando a [CMFCToolBarsCustomizeDialog:: Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), llame a [CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar el botón estándar por el nuevo control.

## <a name="example-creating-a-find-combo-box"></a>Ejemplo: Crear un cuadro combinado buscar

En esta sección se describe cómo crear un control de cuadro combinado **Buscar** que aparece en una barra de herramientas y contiene cadenas de búsqueda usadas recientemente. El usuario puede escribir una cadena en el control y, después, presionar la tecla Entrar para buscar un documento o presionar la tecla Escape para devolver el foco al marco principal. En este ejemplo se da por supuesto que el documento se muestra en una vista derivada de la [clase CEditView](../mfc/reference/ceditview-class.md).

### <a name="creating-the-find-control"></a>Crear el control Buscar

En primer lugar, cree el control de cuadro combinado **Buscar** :

1. Agregue el botón y los comandos a los recursos de la aplicación:

   1. En los recursos de la aplicación, agregue un nuevo botón con un id. de comando `ID_EDIT_FIND` a una barra de herramientas de la aplicación y a los mapas de bits asociados a la barra de herramientas.

   1. Cree un nuevo elemento de menú con `ID_EDIT_FIND` el identificador de comando.

   1. Agregue una nueva cadena "Buscar el texto\nBuscar" a la tabla de cadenas y asígnele un id. de comando `ID_EDIT_FIND_COMBO`. Este identificador se usará como el identificador de comando del botón de cuadro combinado **Buscar** .

        > [!NOTE]
        > Dado que `ID_EDIT_FIND` es un comando estándar que se procesa mediante `CEditView`, no es necesario implementar un controlador especial para este comando.  Sin embargo, debe implementar un controlador para el nuevo comando `ID_EDIT_FIND_COMBO`.

1. Cree una nueva clase, `CFindComboBox`, derivada de la [clase CComboBox](../mfc/reference/ccombobox-class.md).

1. En la clase `CFindComboBox`, invalide el método virtual `PreTranslateMessage`. Este método permitirá que el cuadro combinado procese el mensaje [WM_KEYDOWN](/windows/win32/inputdev/wm-keydown) . Si el usuario presiona la tecla Escape (`VK_ESCAPE`), devuelve el foco a la ventana marco principal. Si el usuario presiona la tecla Entrar (`VK_ENTER`), envía a la ventana marco principal un mensaje de `WM_COMMAND` que contiene el id. de comando `ID_EDIT_FIND_COMBO`.

1. Cree una clase para el botón de cuadro combinado **Buscar** , derivado de la [clase CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). En este ejemplo, se denomina `CFindComboButton`.

1. El constructor de `CMFCToolbarComboBoxButton` toma tres parámetros: el id. de comando del botón, el índice de la imagen del botón y el estilo del cuadro combinado. Establezca estos parámetros de la siguiente forma:

   1. Pase `ID_EDIT_FIND_COMBO` como el id. de comando.

   1. Use [CCommandManager:: GetCmdImage](reference/internal-classes.md) con `ID_EDIT_FIND` para obtener el índice de la imagen.

   1. Para obtener una lista de los estilos de cuadro combinado disponibles, vea [estilos de cuadro combinado](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. En la clase `CFindComboButton`, invalide el método `CMFCToolbarComboBoxButton::CreateCombo`. Aquí se debe crear el objeto `CFindComboButton` y devolver un puntero a él.

1. Utilice la macro [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) para hacer que el botón combinado sea persistente. El administrador del área de trabajo carga y guarda automáticamente el estado del botón en el Registro de Windows.

1. Implemente el controlador `ID_EDIT_FIND_COMBO` en la vista del documento. Use [CMFCToolBar:: GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) con `ID_EDIT_FIND_COMBO` para recuperar todos los botones del cuadro combinado de **búsqueda** . Puede haber varias copias de un botón con el mismo id. de comando debido a la personalización.

1. En el `ID_EDIT_FIND` `OnFind`controlador de mensajes, use [CMFCToolBar:: IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) para determinar si el comando Buscar se envió desde el botón **Buscar** cuadro combinado. Si es así, busque el texto y agregue la cadena de búsqueda al cuadro combinado.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Agregar el control Buscar a la barra de herramientas principal

Para agregar el botón de cuadro combinado a la barra de herramientas, siga estos pasos:

1. Implemente el controlador de mensajes `AFX_WM_RESETTOOLBAR` de `OnToolbarReset` en la ventana marco principal.

    > [!NOTE]
    > El marco envía este mensaje a la ventana marco principal cuando se inicializa una barra de herramientas durante el inicio de la aplicación o cuando se restaura una barra de herramientas durante la personalización. En cualquier caso, debe reemplazar el botón de la barra de herramientas estándar por el botón de cuadro combinado de **búsqueda** personalizada.

1. En el `AFX_WM_RESETTOOLBAR` controlador, examine el identificador de la barra de herramientas, es decir, el *wParam* del mensaje AFX_WM_RESETTOOLBAR. Si el identificador de la barra de herramientas es igual al de la barra de herramientas que contiene el botón **Buscar** cuadro combinado, llame a [CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) para reemplazar el botón **Buscar** (es decir, `ID_EDIT_FIND)` el botón `CFindComboButton` con el identificador de comando por un objeto.

    > [!NOTE]
    > Puede crear un objeto `CFindComboBox` en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Agregar el control Buscar al cuadro de diálogo Personalizar

`OnViewCustomize`En el controlador de personalización, llame a [CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar el botón **Buscar** (es decir, el botón con el `ID_EDIT_FIND`identificador de comando `CFindComboButton` ) con un objeto.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../mfc/hierarchy-chart.md)<br/>
[Clases](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (clase)](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog (clase)](../mfc/reference/cmfctoolbarscustomizedialog-class.md)

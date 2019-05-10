---
title: 'Tutorial: Insertar controles en barras de herramientas'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: f3e4653d1be2f4a1830288ba724d20ddb7610958
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558153"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Tutorial: Insertar controles en barras de herramientas

En este artículo se describe cómo agregar un botón de barra de herramientas que contiene un control de Windows para una barra de herramientas. En MFC, debe ser un botón de barra de herramientas un [CMFCToolBarButton (clase)](../mfc/reference/cmfctoolbarbutton-class.md)-clase derivada, por ejemplo [CMFCToolBarComboBoxButton (clase)](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton (clase)](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton (clase)](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), o [CMFCToolBarMenuButton (clase)](../mfc/reference/cmfctoolbarmenubutton-class.md).

## <a name="adding-controls-to-toolbars"></a>Agregar controles a barras de herramientas

Para agregar un control a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas. Para obtener más información acerca de cómo crear botones mediante el **barra de herramientas del Editor** en Visual Studio, consulte el [barra de herramientas del Editor](../windows/toolbar-editor.md) artículo.

1. Reserve una imagen de la barra de herramientas (icono de botón) para el botón en todos los mapas de bits de la barra de herramientas principal.

1. En el controlador de mensajes que procesa el `AFX_WM_RESETTOOLBAR` de mensajes, realice los pasos siguientes:

   1. Crear el control de botón mediante una clase derivada de `CMFCToolbarButton`.

   1. Reemplazar el botón ficticio por el nuevo control mediante [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Puede crear el objeto del botón en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.

> [!NOTE]
>  Si ha habilitado la personalización de la aplicación, es posible que deba restablecer la barra de herramientas mediante el **restablecer** situado en la **las barras de herramientas** pestaña de la **personalizar** cuadro de diálogo para ver el control actualizado en la aplicación después de volver a compilar. El estado de la barra de herramientas se guarda en el Registro de Windows y la información del Registro se carga y se aplica después de que el método `ReplaceButton` se ejecute durante el inicio de la aplicación.

## <a name="toolbar-controls-and-customization"></a>Controles de barra de herramientas y personalización

El **comandos** pestaña de la **personalizar** cuadro de diálogo contiene una lista de comandos que están disponibles en la aplicación. De forma predeterminada, el **personalizar** cuadro de diálogo procesa los menús de la aplicación y compila una lista de botones de barra de herramientas estándar en cada categoría de menú. Para mantener la funcionalidad extendida que proporcionan los controles de barra de herramientas, debe reemplazar el botón de barra de herramientas estándar con el control personalizado en el **personalizar** cuadro de diálogo.

Cuando se habilita la personalización, crea el **personalizar** cuadro de diálogo en el controlador de personalización `OnViewCustomize` utilizando el [CMFCToolBarsCustomizeDialog (clase)](../mfc/reference/cmfctoolbarscustomizedialog-class.md) clase. Antes de mostrar el **personalizar** cuadro de diálogo mediante una llamada a [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar el botón estándar con el nuevo control.

## <a name="example-creating-a-find-combo-box"></a>Ejemplo: Creación de un cuadro combinado de búsqueda

En esta sección se describe cómo crear un **buscar** control de cuadro combinado que aparece en una barra de herramientas y contiene las cadenas de búsqueda recientes usadas. El usuario puede escribir una cadena en el control y, después, presionar la tecla Entrar para buscar un documento o presionar la tecla Escape para devolver el foco al marco principal. En este ejemplo se da por supuesto que el documento se muestra en un [clase CEditView](../mfc/reference/ceditview-class.md)-vista derivada.

### <a name="creating-the-find-control"></a>Crear el control Buscar

En primer lugar, cree el **buscar** control de cuadro combinado:

1. Agregue el botón y los comandos a los recursos de la aplicación:

   1. En los recursos de la aplicación, agregue un nuevo botón con un id. de comando `ID_EDIT_FIND` a una barra de herramientas de la aplicación y a los mapas de bits asociados a la barra de herramientas.

   1. Crear un nuevo elemento de menú con el `ID_EDIT_FIND` identificador de comando.

   1. Agregue una nueva cadena "Buscar el texto\nBuscar" a la tabla de cadenas y asígnele un id. de comando `ID_EDIT_FIND_COMBO`. Este identificador se utilizará como el identificador del comando el **buscar** botón de cuadro combinado.

        > [!NOTE]
        > Dado que `ID_EDIT_FIND` es un comando estándar que se procesa mediante `CEditView`, no es necesario implementar un controlador especial para este comando.  Sin embargo, debe implementar un controlador para el nuevo comando `ID_EDIT_FIND_COMBO`.

1. Cree una nueva clase, `CFindComboBox`, derivada de [CComboBox (clase)](../mfc/reference/ccombobox-class.md).

1. En la clase `CFindComboBox`, invalide el método virtual `PreTranslateMessage`. Este método habilitará el cuadro combinado para procesar el [WM_KEYDOWN](/windows/desktop/inputdev/wm-keydown) mensaje. Si el usuario presiona la tecla Escape (`VK_ESCAPE`), devuelve el foco a la ventana marco principal. Si el usuario presiona la tecla Entrar (`VK_ENTER`), envía a la ventana marco principal un mensaje de `WM_COMMAND` que contiene el id. de comando `ID_EDIT_FIND_COMBO`.

1. Cree una clase para el **buscar** botón de cuadro combinado, derivado de [CMFCToolBarComboBoxButton (clase)](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). En este ejemplo, se denomina `CFindComboButton`.

1. El constructor de `CMFCToolbarComboBoxButton` toma tres parámetros: el id. de comando del botón, el índice de la imagen del botón y el estilo del cuadro combinado. Establezca estos parámetros de la siguiente forma:

   1. Pase `ID_EDIT_FIND_COMBO` como el id. de comando.

   1. Use [CCommandManager::GetCmdImage](reference/internal-classes.md) con `ID_EDIT_FIND` para obtener el índice de imagen.

   1. Para obtener una lista de estilos de cuadro combinado disponibles, consulte [estilos de cuadro combinado](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. En la clase `CFindComboButton`, invalide el método `CMFCToolbarComboBoxButton::CreateCombo`. Aquí se debe crear el objeto `CFindComboButton` y devolver un puntero a él.

1. Use la [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) macro para que sea el botón combinado sea persistente. El administrador del área de trabajo carga y guarda automáticamente el estado del botón en el Registro de Windows.

1. Implemente el controlador `ID_EDIT_FIND_COMBO` en la vista del documento. Use [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) con `ID_EDIT_FIND_COMBO` para recuperar todos **buscar** botones del cuadro combinado. Puede haber varias copias de un botón con el mismo id. de comando debido a la personalización.

1. En el `ID_EDIT_FIND` controlador de mensajes `OnFind`, utilice [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) para determinar si se ha enviado el comando Buscar desde el **buscar** botón de cuadro combinado. Si es así, busque el texto y agregue la cadena de búsqueda al cuadro combinado.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Agregar el control Buscar a la barra de herramientas principal

Para agregar el botón de cuadro combinado a la barra de herramientas, siga estos pasos:

1. Implemente el controlador de mensajes `AFX_WM_RESETTOOLBAR` de `OnToolbarReset` en la ventana marco principal.

    > [!NOTE]
    > El marco envía este mensaje a la ventana marco principal cuando se inicializa una barra de herramientas durante el inicio de la aplicación o cuando se restaura una barra de herramientas durante la personalización. En cualquier caso, debe reemplazar el botón de barra de herramientas estándar con personalizado **buscar** botón de cuadro combinado.

1. En el `AFX_WM_RESETTOOLBAR` controlador, examine el identificador de la barra de herramientas, es decir, el *WPARAM* del mensaje AFX_WM_RESETTOOLBAR. Si el identificador de la barra de herramientas es igual al de la barra de herramientas que contiene el **buscar** botón de cuadro combinado, llame al [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) para reemplazar el **encontrar** botón (es decir, el botón con el identificador de comando `ID_EDIT_FIND)` con un `CFindComboButton` objeto.

    > [!NOTE]
    > Puede crear un objeto `CFindComboBox` en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Agregar el control Buscar al cuadro de diálogo Personalizar

En el controlador de personalización `OnViewCustomize`, llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar el **buscar** botón (es decir, el botón con el identificador de comando `ID_EDIT_FIND`) con un `CFindComboButton` objeto.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../mfc/hierarchy-chart.md)<br/>
[Clases](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (clase)](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog (clase)](../mfc/reference/cmfctoolbarscustomizedialog-class.md)

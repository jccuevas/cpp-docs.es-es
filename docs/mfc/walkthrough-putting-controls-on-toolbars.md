---
title: 'Tutorial: Poner controles en las barras de herramientas'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 2a801e61c49301d9b8780bbf7eb77025990337ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360266"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Tutorial: Poner controles en las barras de herramientas

En este artículo se describe cómo agregar un botón de barra de herramientas que contiene un control de Windows a una barra de herramientas. En MFC, un botón de barra de herramientas debe ser una clase derivada de [CMFCToolBarButton (Clase),](../mfc/reference/cmfctoolbarbutton-class.md)por ejemplo [CMFCToolBarComboBoxButton (Clase)](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton (Clase)](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton (Clase)](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)o [CMFCToolBarMenuButton (Clase).](../mfc/reference/cmfctoolbarmenubutton-class.md)

## <a name="adding-controls-to-toolbars"></a>Agregar controles a barras de herramientas

Para agregar un control a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas. Para obtener más información acerca de cómo crear botones mediante el **Editor** de barra de herramientas en Visual Studio, vea el [artículo Editor](../windows/toolbar-editor.md) de barra de herramientas.

1. Reserve una imagen de la barra de herramientas (icono de botón) para el botón en todos los mapas de bits de la barra de herramientas principal.

1. En el controlador de `AFX_WM_RESETTOOLBAR` mensajes que procesa el mensaje, siga estos pasos:

   1. Crear el control de botón mediante una clase derivada de `CMFCToolbarButton`.

   1. Reemplace el botón ficticio por el nuevo control mediante [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Puede crear el objeto del botón en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.

> [!NOTE]
> Si ha habilitado la personalización en la aplicación, es posible que tenga que restablecer la barra de herramientas mediante el botón **Restablecer** de la pestaña **Barras** de herramientas del cuadro de diálogo **Personalizar** para ver el control actualizado en la aplicación después de volver a compilar. El estado de la barra de herramientas se guarda en el Registro de Windows y la información del Registro se carga y se aplica después de que el método `ReplaceButton` se ejecute durante el inicio de la aplicación.

## <a name="toolbar-controls-and-customization"></a>Controles de barra de herramientas y personalización

La pestaña **Comandos** del cuadro de diálogo **Personalizar** contiene una lista de comandos que están disponibles en la aplicación. De forma predeterminada, el cuadro de diálogo **Personalizar** procesa los menús de la aplicación y crea una lista de botones de barra de herramientas estándar en cada categoría de menú. Para mantener la funcionalidad extendida que proporcionan los controles de barra de herramientas, debe reemplazar el botón de barra de herramientas estándar con el control personalizado en el cuadro de diálogo **Personalizar.**

Cuando se habilita la **Customize** personalización, se crea `OnViewCustomize` el personalizar cuadro de diálogo en el controlador de personalización mediante el [CMFCToolBarsCustomizeDialog clase.](../mfc/reference/cmfctoolbarscustomizedialog-class.md) Antes de mostrar el **personalizar** cuadro de diálogo mediante una llamada a [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar el botón estándar con el nuevo control.

## <a name="example-creating-a-find-combo-box"></a>Ejemplo: Crear un cuadro combinado de búsqueda

En esta sección se describe cómo crear un control de cuadro combinado **Buscar** que aparece en una barra de herramientas y contiene cadenas de búsqueda usadas recientemente. El usuario puede escribir una cadena en el control y, después, presionar la tecla Entrar para buscar un documento o presionar la tecla Escape para devolver el foco al marco principal. En este ejemplo se supone que el documento se muestra en una vista derivada de [la clase CEditView.](../mfc/reference/ceditview-class.md)

### <a name="creating-the-find-control"></a>Crear el control Buscar

En primer lugar, cree el control de cuadro combinado **Buscar:**

1. Agregue el botón y los comandos a los recursos de la aplicación:

   1. En los recursos de la aplicación, agregue un nuevo botón con un id. de comando `ID_EDIT_FIND` a una barra de herramientas de la aplicación y a los mapas de bits asociados a la barra de herramientas.

   1. Cree un nuevo elemento `ID_EDIT_FIND` de menú con el identificador de comando.

   1. Agregue una nueva cadena "Buscar el texto\nBuscar" a la tabla de cadenas y asígnele un id. de comando `ID_EDIT_FIND_COMBO`. Este ID se utilizará como identificador de comando del botón de cuadro combinado **Buscar.**

        > [!NOTE]
        > Dado que `ID_EDIT_FIND` es un comando estándar que se procesa mediante `CEditView`, no es necesario implementar un controlador especial para este comando.  Sin embargo, debe implementar un controlador para el nuevo comando `ID_EDIT_FIND_COMBO`.

1. Cree una nueva `CFindComboBox`clase, , derivada de [CComboBox (Clase).](../mfc/reference/ccombobox-class.md)

1. En la clase `CFindComboBox`, invalide el método virtual `PreTranslateMessage`. Este método habilitará el cuadro combinado para procesar el [mensaje de WM_KEYDOWN.](/windows/win32/inputdev/wm-keydown) Si el usuario presiona la tecla Escape (`VK_ESCAPE`), devuelve el foco a la ventana marco principal. Si el usuario presiona la tecla Entrar (`VK_ENTER`), envía a la ventana marco principal un mensaje de `WM_COMMAND` que contiene el id. de comando `ID_EDIT_FIND_COMBO`.

1. Cree una clase para el botón de cuadro combinado **Buscar,** derivada de [CMFCToolBarComboBoxButton (Clase).](../mfc/reference/cmfctoolbarcomboboxbutton-class.md) En este ejemplo, se denomina `CFindComboButton`.

1. El constructor de `CMFCToolbarComboBoxButton` toma tres parámetros: el id. de comando del botón, el índice de la imagen del botón y el estilo del cuadro combinado. Establezca estos parámetros de la siguiente forma:

   1. Pase `ID_EDIT_FIND_COMBO` como el id. de comando.

   1. Utilice [CCommandManager::GetCmdImage](reference/internal-classes.md) con `ID_EDIT_FIND` para obtener el índice de imagen.

   1. Para obtener una lista de los estilos de cuadro combinado disponibles, vea [Estilos de cuadro](../mfc/reference/styles-used-by-mfc.md#combo-box-styles)combinado .

1. En la clase `CFindComboButton`, invalide el método `CMFCToolbarComboBoxButton::CreateCombo`. Aquí se debe crear el objeto `CFindComboButton` y devolver un puntero a él.

1. Utilice la macro [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) para que el botón combinado sea persistente. El administrador del área de trabajo carga y guarda automáticamente el estado del botón en el Registro de Windows.

1. Implemente el controlador `ID_EDIT_FIND_COMBO` en la vista del documento. Utilice [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) con `ID_EDIT_FIND_COMBO` para recuperar todos los botones del cuadro combinado **Buscar.** Puede haber varias copias de un botón con el mismo id. de comando debido a la personalización.

1. En `ID_EDIT_FIND` el `OnFind`controlador de mensajes , utilice [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) para determinar si el comando find se envió desde el botón de cuadro combinado **Buscar.** Si es así, busque el texto y agregue la cadena de búsqueda al cuadro combinado.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Agregar el control Buscar a la barra de herramientas principal

Para agregar el botón de cuadro combinado a la barra de herramientas, siga estos pasos:

1. Implemente el controlador de mensajes `AFX_WM_RESETTOOLBAR` de `OnToolbarReset` en la ventana marco principal.

    > [!NOTE]
    > El marco envía este mensaje a la ventana marco principal cuando se inicializa una barra de herramientas durante el inicio de la aplicación o cuando se restaura una barra de herramientas durante la personalización. En cualquier caso, debe reemplazar el botón de barra de herramientas estándar con el botón personalizado del cuadro combinado **Buscar.**

1. En `AFX_WM_RESETTOOLBAR` el controlador, examine el identificador de la barra de herramientas, es decir, el *WPARAM* del mensaje de AFX_WM_RESETTOOLBAR. Si el identificador de barra de herramientas es igual al de la barra de herramientas que **Find** contiene el botón de cuadro `ID_EDIT_FIND)` combinado `CFindComboButton` **Buscar,** llame a [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) para reemplazar el botón Buscar (es decir, el botón con el identificador de comando con un objeto.

    > [!NOTE]
    > Puede crear un objeto `CFindComboBox` en la pila, porque `ReplaceButton` copia el objeto Button y mantiene la copia.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Agregar el control Buscar al cuadro de diálogo Personalizar

En el `OnViewCustomize`controlador de personalización , llame a [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) para reemplazar `ID_EDIT_FIND`el `CFindComboButton` botón **Buscar** (es decir, el botón con el identificador de comando ) con un objeto.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../mfc/hierarchy-chart.md)<br/>
[Clases](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (Clase)](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog (Clase)](../mfc/reference/cmfctoolbarscustomizedialog-class.md)

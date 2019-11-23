---
title: Editor de barrasC++de herramientas ()
ms.date: 02/14/2019
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 72c42a06da8276d118c6c204f838ed4b31d142b9
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "69514691"
---
# <a name="toolbar-editor-c"></a>Editor de barrasC++de herramientas ()

El **Editor** de la barra de herramientas permite crear recursos de barra de herramientas y convertir mapas de bits en recursos de barra de herramientas. El **Editor** de la barra de herramientas usa una presentación gráfica para mostrar una barra de herramientas y botones que se parecen mucho a la apariencia de una aplicación finalizada.

La ventana del editor de la **barra de herramientas** muestra dos vistas de una imagen de botón, igual que la ventana del **Editor de imágenes** . Una barra de división separa los dos paneles y puede arrastrar la barra de división de lado a lado para cambiar los tamaños relativos de los paneles. El panel activo muestra un borde de selección y encima de las dos vistas de la imagen es la barra de herramientas del asunto.

![Editor de barras de herramientas](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**Editor de barras de herramientas**

El **Editor** de la barra de herramientas es similar al **Editor de imágenes** en la funcionalidad de y los elementos de menú, las herramientas gráficas y la cuadrícula de mapa de bits entre ambos son los mismos. Hay un comando de menú en el menú **imagen** para cambiar entre el **Editor** de la barra de herramientas y el **Editor de imágenes**. Para obtener más información sobre el uso de la barra de herramientas de **gráficos** , la paleta de **colores** o el menú **imagen** , vea [Editor de imágenes](../windows/image-editor-for-icons.md).

Puede crear una nueva barra de herramientas en C++ un proyecto mediante la conversión de un mapa de bits. El gráfico del mapa de bits se convierte en las imágenes de botón de una barra de herramientas. Normalmente, el mapa de bits contiene varias imágenes de botón en un único mapa de bits, con una imagen para cada botón. Las imágenes pueden tener cualquier tamaño, ya que el valor predeterminado es de 16 píxeles de ancho y el alto de la imagen. Puede especificar el tamaño de las imágenes de botón en el cuadro de diálogo **nuevo recurso** de la barra de herramientas al elegir **Editor de barras de herramientas** en el menú **imagen** , en el **Editor de imágenes**.

El cuadro de diálogo **nuevo recurso** de la barra de herramientas permite especificar el ancho y el alto de los botones que se van a agregar C++ a un recurso de la barra de herramientas de un proyecto. El valor predeterminado es 16 × 15 píxeles.

Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048, por lo que si establece el **ancho del botón** en *512*, solo puede tener cuatro botones. Si establece el ancho en *513*, solo puede tener tres botones.

El cuadro de diálogo **nuevo recurso** de la barra de herramientas tiene las siguientes propiedades:

|Propiedad|Descripción|
|---|---------------|
|**Ancho del botón**|Proporciona un espacio para que escriba el ancho de los botones de la barra de herramientas que va a convertir de un recurso de mapa de bits a un recurso de la barra de herramientas.|
|**Alto del botón**|Proporciona un espacio para que escriba el alto de los botones de la barra de herramientas que va a convertir de un recurso de mapa de bits a un recurso de la barra de herramientas.|

> [!NOTE]
> Las imágenes se recortan hasta el ancho y el alto especificados, y los colores se ajustan para usar los colores de la barra de herramientas estándar (16 colores).

De forma predeterminada, se muestra un botón nuevo o en blanco en el extremo derecho de la barra de herramientas. Puede desplace este botón antes de editarlo. Al crear un nuevo botón, aparece otro botón en blanco a la derecha del botón editado. Al guardar una barra de herramientas, no se guarda el botón en blanco.

Un botón de la barra de herramientas tiene las siguientes propiedades:

|Propiedad|Descripción|
|--------------|-----------------|
|**Id.**|Define el identificador del botón. La lista desplegable proporciona nombres de **identificador** comunes.|
|**Width**|Establece el ancho del botón. se recomienda 16 píxeles.|
|**Height**|Establece el alto del botón. El alto de un botón cambia el alto de todos los botones de la barra de herramientas. se recomiendan 15 píxeles.|
|**Preguntar**|Define el mensaje que se muestra en la barra de estado. Al agregar *\n* y un nombre, se agrega una **información sobre herramientas** a ese botón de la barra de herramientas. Para obtener más información, vea [crear una información sobre herramientas](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

El **ancho** y el **alto** se aplican a todos los botones. Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048, por lo que si establece el ancho del botón en *512*, solo podrá tener cuatro botones y, si establece el ancho en *513*, solo podrá tener tres botones.

## <a name="how-to"></a>Procedimientos

El **Editor** de la barra de herramientas le permite:

### <a name="to-create-new-toolbars"></a>Para crear nuevas barras de herramientas

1. En **vista de recursos**, haga clic con el botón derecho en el archivo *. RC* y elija **Agregar recurso**. Si ya tiene una barra de herramientas en el archivo *. RC* , puede hacer clic con el botón secundario en la carpeta de la **barra de herramientas** y seleccionar **Insertar barra de herramientas**.

1. En el cuadro de diálogo **Agregar recurso** , seleccione **barra de herramientas** en la lista tipo de **recurso** y, a continuación, elija **nuevo**.

   Si aparece un signo más ( **+** ) junto al tipo de recurso de la **barra de herramientas** , significa que las plantillas de barra de herramientas están disponibles. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **nuevo**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Para convertir mapas de bits en recursos de barra de herramientas

1. Abra un recurso de mapa de bits existente en el [Editor de imágenes](../windows/image-editor-for-icons.md). Si el mapa de bits todavía no está en el archivo *. RC* , haga clic con el botón derecho en el archivo *. RC* y elija **importar**y, a continuación, desplácese hasta el mapa de bits que desee agregar al archivo *. RC* y seleccione **abrir**.

1. Vaya a la **imagen** de menú > **Editor de barras de herramientas**.

   Aparece el cuadro de diálogo **nuevo recurso** de la barra de herramientas. Puede cambiar el ancho y el alto de las imágenes de icono para que coincidan con el mapa de bits. La imagen de la barra de herramientas se muestra a continuación en el editor de la **barra de herramientas**.

1. Para finalizar la conversión, cambie el **identificador** de comando del botón mediante el [ventana Propiedades](/visualstudio/ide/reference/properties-window). Escriba el nuevo *identificador* o seleccione un **identificador** de la lista desplegable.

   > [!TIP]
   > La ventana **propiedades** contiene un botón de alfiler en la barra de título y, al seleccionar esta opción, se habilita o deshabilita **Ocultar automáticamente** para la ventana. Para recorrer todas las propiedades del botón de la barra de herramientas sin tener que volver a abrir las ventanas de propiedades individuales, desactive **Ocultar automáticamente** , de modo que la ventana **propiedades** permanezca inmóvil.

   También puede cambiar los identificadores de comando de los botones de la nueva barra de herramientas mediante el [ventana Propiedades](/visualstudio/ide/reference/properties-window).

### <a name="to-manage-toolbar-buttons"></a>Para administrar los botones de la barra de herramientas

#### <a name="to-create-a-new-toolbar-button"></a>Para crear un nuevo botón de la barra de herramientas

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) expanda la carpeta de recursos (por ejemplo, *Project1. RC*).

1. Expanda la carpeta **barra de herramientas** y seleccione una barra de herramientas para editarla y, a continuación, realice una de las acciones siguientes:

   - Asigne un identificador al botón en blanco que se encuentra en el extremo derecho de la barra de herramientas. Puede hacerlo editando la propiedad **ID** en la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Por ejemplo, puede que desee asignar al botón de la barra de herramientas el mismo identificador que una opción de menú. En este caso, use el cuadro de lista desplegable para seleccionar el **identificador** de la opción de menú.

   - Seleccione el botón en blanco situado en el extremo derecho de la barra de herramientas en el panel vista de la **barra de herramientas** y comience a dibujar. Se asigna un identificador de comando de botón predeterminado (ID_BUTTON\<n >).

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Para agregar una imagen a una barra de herramientas como un botón

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga doble clic en la barra de herramientas para abrirla.

1. A continuación, abra la imagen que le gustaría agregar a la barra de herramientas.

   > [!NOTE]
   > Si abre la imagen en Visual Studio, se abrirá en el editor de **imágenes**. También puede abrir la imagen en otros programas de gráficos.

1. Vaya a menú **editar** > **copiar**.

1. Cambie a la barra de herramientas; para ello, seleccione su pestaña en la parte superior de la ventana de código fuente.

1. Vaya a menú **editar** > **pegar**.

   La imagen aparecerá en la barra de herramientas como un botón nuevo.

#### <a name="to-move-a-toolbar-button"></a>Para desplace un botón de la barra de herramientas

En el panel de vista de la **barra de herramientas** , arrastre el botón que desea desplace a su nueva ubicación en la barra de herramientas.

- Para copiar botones de una barra de herramientas, mantenga presionada la tecla **Ctrl** y, en el panel de vista de la **barra de herramientas** , arrastre el botón hasta su nueva ubicación en la barra de herramientas o hasta una ubicación en otra barra de herramientas.

- Para eliminar un botón de la barra de herramientas, seleccione el botón de la barra de herramientas y arrástrelo fuera de la barra de herramientas.

- Para insertar o quitar espacio entre los botones de una barra de herramientas, arrástrelos hacia delante o hacia el otro en la barra de herramientas.

|Acción|Paso|
|------|------|
|Para insertar un espacio antes de un botón que no está seguido de un espacio|Arrastre el botón hacia la derecha o hacia abajo hasta que se solape con el botón siguiente aproximadamente a la mitad.|
|Para insertar un espacio antes de un botón seguido de un espacio y mantener el espacio al final|Arrastre el botón hasta que el borde derecho o inferior solo toque el botón siguiente o simplemente se superponga.|
|Para insertar un espacio antes de un botón seguido de un espacio y cerrar el siguiente espacio|Arrastre el botón hacia la derecha o hacia abajo hasta que se solape con el botón siguiente aproximadamente a la mitad.|
|Para quitar un espacio entre los botones de una barra de herramientas|Arrastre el botón de un lado del espacio hacia el botón situado en el otro lado del espacio hasta que se solape con el botón siguiente sobre la mitad.|

> [!NOTE]
> Si no hay espacio en el lateral del botón al que está arrastrando y arrastra el botón más allá de la mitad del botón adyacente, el editor de la **barra de herramientas** inserta un espacio en el lado opuesto del botón que está arrastrando.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>Para cambiar las propiedades de un botón de la barra de herramientas

1. En un C++ proyecto de, seleccione el botón de la barra de herramientas.

1. Escriba el nuevo identificador en la propiedad **ID** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window), o use la lista desplegable para seleccionar un nuevo **identificador**.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Para crear una información sobre herramientas para un botón de la barra de herramientas

1. Seleccione el botón de la barra de herramientas.

1. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), en el campo **prompt** , agregue una descripción del botón de la barra de estado y, después del mensaje, agregue `\n` y el nombre de la información sobre herramientas.

Por ejemplo, para ver la información sobre herramientas del botón **Imprimir** en **WordPad**:

1. Abra **WordPad**.

1. Mantenga el puntero del mouse sobre el botón **Imprimir** de la barra de herramientas y observe que la palabra `Print` ahora es flotante debajo del puntero del mouse.

1. Fíjese en la barra de estado en la parte inferior de la ventana de **WordPad** y observe que ahora se muestra el texto `Prints the active document`.

`Print` es el nombre de la información sobre herramientas y `Prints the active document` es la descripción del botón de la barra de estado.

Si desea este efecto mediante el editor de la **barra de herramientas**, establezca la propiedad **prompt** en `Prints the active document\nPrint`.

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)
[Menús y otros recursos](/windows/win32/menurc/resources)<br/>
[Propiedades de los botones de la barra de herramientas](../windows/toolbar-button-properties.md)<br/>

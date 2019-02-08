---
title: Barra de herramientas del Editor (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 61b4d3ba6fc70e78c6f794528822eb66fb94de7e
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905789"
---
# <a name="toolbar-editor-c"></a>Barra de herramientas del Editor (C++)

El **barra de herramientas** editor le permite crear recursos de la barra de herramientas de C++ y convertir mapas de bits en recursos de la barra de herramientas. El **barra de herramientas** editor usa una presentación gráfica para mostrar una barra de herramientas y botones que se parecen mucho al aspecto que deberá en una aplicación acabada.

El **barra de herramientas** ventana del editor muestra dos vistas de una imagen del botón, igual que la ventana del editor de imágenes. Una barra de división separa los dos paneles. Se puede arrastrar dicha barra a uno u otro lado para cambiar el tamaño relativo de los paneles. El panel activo muestra un borde de selección. Por encima de las dos vistas de la imagen se encuentra la barra de herramientas del asunto.

![Editor de la barra de herramientas](../mfc/media/vctoolbareditor.gif "vcToolbarEditor") barra de herramientas del Editor

El **barra de herramientas** editor es similar a la **imagen** editor en la funcionalidad. Los elementos de menú, las herramientas gráficas y cuadrícula de mapa de bits son los mismos que los de la **imagen** editor. Hay un comando de menú en el **imagen** menú para que pueda cambiar entre el **barra de herramientas** editor y la **imagen** editor. Para obtener más información sobre el uso de la **gráficos** barra de herramientas, **colores** paleta, o **imagen** menú, vea [Editor de imágenes](../windows/image-editor-for-icons.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

Con el **barra de herramientas** editor, puede:

## <a name="create-new-toolbars"></a>Crear nuevas barras de herramientas

1. En **recursos** ver, haga clic en el archivo .rc y, a continuación, elija **Agregar recurso** en el menú contextual. (Si tiene una barra de herramientas existente en el archivo .rc, puede hacer simplemente clic en el **barra de herramientas** carpeta y seleccione **insertar Toolbar** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el **Agregar recurso** cuadro de diálogo, seleccione **barra de herramientas** en el **tipo de recurso** lista y luego elija **New**.

   Si un signo más (**+**) aparece junto a la **barra de herramientas** tipo de recurso, significa que están disponibles plantillas de barra de herramientas. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **New**.

## <a name="convert-bitmaps-to-toolbar-resources"></a>Convertir mapas de bits a recursos de la barra de herramientas

Puede crear una nueva barra de herramientas en un proyecto de C++ mediante la conversión de un mapa de bits. El gráfico de mapa de bits se convierte a las imágenes de botón para una barra de herramientas. Normalmente, el mapa de bits contiene varias imágenes de botón en un mapa de bits única, con una imagen para cada botón. Las imágenes pueden tener cualquier tamaño como el valor predeterminado es 16 píxeles de ancho y el alto de la imagen. Puede especificar el tamaño de las imágenes de botón en el **nuevo recurso de barra de herramientas** cuadro de diálogo cuando se elige **barra de herramientas del Editor** desde el **imagen** menú mientras está en el editor de imágenes.

El **nuevo recurso de barra de herramientas** cuadro de diálogo permite especificar el ancho y alto de los botones que se va a agregar a un recurso de barra de herramientas en un proyecto de C++. El valor predeterminado es 16 x 15 píxeles.

Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048. Por tanto, si establece la **ancho del botón** en 512, solo puede tener cuatro botones. Si establece el ancho en 513, solo puede tener tres botones.

El cuadro de diálogo tiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**Ancho del botón**|Proporciona un espacio para escribir el ancho de los botones de barra de herramientas que está convirtiendo de un recurso de mapa de bits a un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto especificados, y se ajustan los colores para utilizar colores de la barra de herramientas estándar (16 colores).|
|**Alto de botón**|Proporciona un espacio para escribir el alto de los botones de barra de herramientas que está convirtiendo de un recurso de mapa de bits a un recurso de barra de herramientas. Las imágenes se recortan al ancho y alto especificados, y se ajustan los colores para utilizar colores de la barra de herramientas estándar (16 colores).|

### <a name="to-convert-bitmaps-to-a-toolbar"></a>Convertir mapas de bits a una barra de herramientas

1. Abrir un recurso de mapa de bits existente en el [editor de imágenes](../windows/image-editor-for-icons.md). (Si el mapa de bits no está en el archivo .rc, haga clic en el archivo .rc, elija **importación** en el menú contextual, navegue hasta el mapa de bits que se va a agregar al archivo .rc y luego seleccione **abierto**.)

1. Desde el **imagen** menú, elija **barra de herramientas del Editor**.

   El **nuevo recurso de barra de herramientas** aparece el cuadro de diálogo. Puede cambiar el ancho y alto de las imágenes de icono para que coincida con el mapa de bits. La imagen de la barra de herramientas, a continuación, se muestra en el editor de la barra de herramientas.

1. Para finalizar la conversión, cambie el comando **ID** del botón con el [ventana propiedades](/visualstudio/ide/reference/properties-window). Escriba el nuevo **ID** o seleccione un **ID** en la lista desplegable.

   > [!TIP]
   > El **propiedades** ventana contiene un botón de alfiler en la barra de título. Al seleccionar este botón habilita o deshabilita **Ocultar automáticamente** para la ventana. Para recorrer rápidamente todas las propiedades del botón de barra de herramientas sin tener que volver a abrir las ventanas de propiedades individuales, activar **Ocultar automáticamente** desactivar por lo que la **propiedades** ventana permanece estacionario.

También puede cambiar los identificadores de comando de los botones de la barra de herramientas nueva mediante el [ventana propiedades](/visualstudio/ide/reference/properties-window).

## <a name="create-move-and-edit-toolbar-buttons"></a>Crear, mover y editar botones de la barra de herramientas

Puede crear fácilmente, mover, copiar y editar botones de la barra de herramientas.

De forma predeterminada, se muestra un botón nuevo o en blanco en el extremo derecho de la barra de herramientas. Puede mover este botón antes de editarlo. Cuando se crea un nuevo botón, aparece otro botón en blanco a la derecha del botón editado. Cuando se guarda una barra de herramientas, no se guarda el botón en blanco.

Las propiedades de un botón de barra de herramientas son:

|Property|Descripción|
|--------------|-----------------|
|**ID**|Define el identificador del botón. La lista desplegable proporciona comunes **ID** nombres.|
|**Width**|Establece el ancho del botón. se recomienda 16 píxeles.|
|**Height**|Establece el alto del botón. El alto de un botón cambia el alto de todos los botones de la barra de herramientas. se recomienda 15 píxeles.|
|**Preguntar**|Define el mensaje que se muestra en la barra de estado. Agregar un nombre y \n agrega una información sobre herramientas a ese botón de barra de herramientas. Para obtener más información, consulte [creación de una información sobre herramientas](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Ancho** y **alto** se aplican a todos los botones. Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048. Por lo que si se establece el ancho del botón en 512, solo puede tener cuatro botones y si se establece el ancho en 513, solo puede tener tres botones.

Consulte las siguientes acciones:

### <a name="to-create-a-new-toolbar-button"></a>Para crear un nuevo botón de barra de herramientas

1. En [vista de recursos](../windows/resource-view-window.md) expanda la carpeta de recursos (por ejemplo, *Project1.rc*).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. Expanda el **barra de herramientas** carpeta y seleccione una barra de herramientas para editar.

1. Asignar un identificador al botón en blanco en el extremo derecho de la barra de herramientas. Puede hacerlo mediante la edición de la **ID** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window). Por ejemplo, desea dar a un botón de barra de herramientas en el mismo identificador que una opción de menú. En este caso, utilice el cuadro de lista desplegable para seleccionar el **ID** de la opción de menú.

   O bien

   Seleccione el botón en blanco en el extremo derecho de la barra de herramientas (en el **barra de herramientas Vista** panel) y empezar a dibujar. Se asigna un identificador de comando del botón predeterminado (ID\<n >).

También puede copiar y pegar una imagen en una barra de herramientas como un botón nuevo.

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Para agregar una imagen a una barra de herramientas como un botón

1. En [vista de recursos](../windows/resource-view-window.md), abra la barra de herramientas haciendo doble clic en él.

1. A continuación, abra la imagen que le gustaría agregar a la barra de herramientas.

   > [!NOTE]
   > Si la imagen se abre en Visual Studio, se abrirá en el **imagen** editor. También puede abrir la imagen en otros programas de gráficos.

1. Desde el **editar** menú, elija **copia**.

1. Cambiar a la barra de herramientas seleccionando su pestaña de la parte superior de la ventana de código fuente.

1. Desde el **editar** menú, elija **pegar**.

   La imagen aparecerá en la barra de herramientas como un botón nuevo.

### <a name="to-move-a-toolbar-button"></a>Para mover un botón de barra de herramientas

En el **barra de herramientas Vista** panel, arrastre el botón que desea mover a su nueva ubicación en la barra de herramientas.

### <a name="to-copy-buttons-from-a-toolbar"></a>Copiar botones de una barra de herramientas

1. Mantenga presionada la **Ctrl** clave.

1. En el **barra de herramientas Vista** panel, arrastre el botón a su nueva ubicación en la barra de herramientas o en una ubicación en otra barra de herramientas.

### <a name="to-delete-a-toolbar-button"></a>Para eliminar un botón de barra de herramientas

Seleccione el botón de barra de herramientas y arrástrela fuera de la barra de herramientas.

### <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Para insertar o quitar espacio entre los botones de una barra de herramientas

En general, para insertar un espacio entre los botones, arrástrelos fuera de ellas en la barra de herramientas. Para quitar espacio, arrástrelos hacia entre sí.

|Acción|Paso|
|------|------|
|Para insertar un espacio delante de un botón que no está seguido por un espacio|Arrastre el botón a la derecha o hacia abajo hasta que se superpone sobre el botón siguiente acerca de la mitad.|
|Para insertar un espacio delante de un botón que va seguido de un espacio y mantener el espacio final|Arrastre el botón hasta que el borde derecho o inferior, simplemente es tocar el botón siguiente o se superpone a él.|
|Para insertar un espacio delante de un botón que va seguido de un espacio y cerrar espacio siguiente|Arrastre el botón a la derecha o hacia abajo hasta que se superpone sobre el botón siguiente acerca de la mitad.|
|Para quitar un espacio entre los botones de una barra de herramientas|Arrastre el botón en un lado del espacio hacia el botón del otro lado del espacio hasta que se superponga con el botón siguiente aproximadamente hasta la mitad.|

> [!NOTE]
> Si no hay ningún espacio en el lado del botón que arrastra fuera del, y arrastra el botón más de la mitad pasado el botón adyacente, el **barra de herramientas** editor también inserta un espacio en el lado opuesto del botón que le operación de arrastre.

### <a name="to-change-the-properties-of-a-toolbar-button"></a>Para cambiar las propiedades de un botón de barra de herramientas

1. En un proyecto de C++, seleccione el botón de barra de herramientas.

1. Escriba el nuevo identificador en el **ID** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window), o use la lista desplegable para seleccionar un nuevo **ID**.

### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Para crear una información sobre herramientas para un botón de barra de herramientas

1. Seleccione el botón de barra de herramientas.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), en el **Prompt** campo de propiedad, agregue una descripción del botón de la barra de estado; después del mensaje, agregue `\n` y su nombre.

Un ejemplo común de una información sobre herramientas es el **impresión** botón **WordPad**:

1. Abra **WordPad**.

1. Mantenga el puntero del mouse sobre el **impresión** botón de barra de herramientas.

1. Tenga en cuenta que la palabra `Print` ahora está flotando en el puntero del mouse.

1. Examine la barra de estado (en la parte inferior de la **WordPad** ventana): tenga en cuenta que ahora muestra el texto `Prints the active document`.

El `Print` en **paso 3** es el nombre"herramienta sugerencia" y el `Prints the active document` desde **paso 4** es la "Descripción del botón de la barra de estado".

Si desea que este efecto mediante el **barra de herramientas** editor, establezca el **Prompt** propiedad `Prints the active document\nPrint`.

> [!NOTE]
> Puede editar el texto del mensaje utilizando el [ventana propiedades](/visualstudio/ide/reference/properties-window).

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Menús y otros recursos](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Propiedades de los botones de la barra de herramientas](../windows/toolbar-button-properties.md)<br/>

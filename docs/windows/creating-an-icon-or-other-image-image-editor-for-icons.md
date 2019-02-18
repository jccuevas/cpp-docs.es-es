---
title: Cómo Crear un icono u otra imagen
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 69fffc71a7b5dfad12e70a9132fc61b11a0914cc
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336597"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Cómo Crear un icono u otra imagen

Puede crear una nueva imagen (mapa de bits, icono, cursor o barra de herramientas) y luego usar el editor de imágenes para personalizar su apariencia. También puede crear un nuevo mapa de bits crearse un [plantilla](../windows/how-to-use-resource-templates.md).

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Iconos y cursores: Recursos de imagen para dispositivos de presentación

Los iconos y cursores son recursos gráficos que pueden contener varias imágenes de diferentes tamaños y combinaciones de colores para distintos tipos de dispositivos de pantalla. Además, un cursor tiene una "zona activa", la ubicación de Windows se usa para realizar un seguimiento de su posición. Iconos y cursores se crean y editan mediante el **imagen** editor, como son mapas de bits y otras imágenes.

Cuando se crea un nuevo icono o cursor, la **imagen** editor crea primero una imagen de un tipo estándar. La imagen se rellena inicialmente con el color de la pantalla (transparente). Si la imagen es un cursor, la zona activa es inicialmente la esquina superior izquierda (coordenadas 0,0).

De forma predeterminada, el **imagen** editor es compatible con la creación de imágenes adicionales para los dispositivos que se muestra en la tabla siguiente. Puede crear imágenes para otros dispositivos escribiendo parámetros de ancho, alto y número de colores en el [cuadro de diálogo Imagen personalizada](custom-image-dialog-box-image-editor-for-icons.md).

> [!NOTE]
> Mediante el **Editor de imágenes**, puede ver las imágenes de 32 bits, pero no puede modificarlas.

|Color|Ancho (píxeles)|Alto (píxeles)|
|-----------|----------------------|-----------------------|
|Monocromático|16|16|
|Monocromático|32|32|
|Monocromático|48|48|
|Monocromático|64|64|
|Monocromático|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>Crear una imagen de dispositivo (icono o cursor)

Al crear un nuevo icono o cursor, la **imagen** editor crea primero una imagen en un estilo específico (32 x 32, 16 colores para iconos y 32 x 32, monocromático para cursores). A continuación, puede agregar imágenes de diferentes tamaños y estilos para el icono o cursor inicial y edite cada imagen adicional, según sea necesario, para los dispositivos de pantalla diferentes. También puede editar una imagen mediante una operación de cortar y pegar desde un tipo de imagen existente o desde un mapa de bits creados en un programa de gráficos.

Al abrir el recurso de icono o cursor en el [editor de imágenes](../windows/image-editor-for-icons.md), la imagen de la mayoría coincidiendo casi con el dispositivo de pantalla actual se abre de forma predeterminada.

El **New &lt;dispositivo&gt; tipo de imagen** cuadro de diálogo le permite crear una nueva imagen de dispositivo de un tipo especificado. Para abrir el **New \<dispositivo > imagen** cuadro de diálogo, seleccione **nuevo tipo de imagen** en el **imagen** menú. Son las siguientes propiedades incluidas **tipo de imagen de destino** y **personalizado**.

El **tipo de imagen de destino** listas de propiedades de los tipos de imágenes disponibles. Seleccione el tipo de imagen que desea abrir:

||||
|-|-|-|
|-16 x 16, 16 colores|-48 x 48, 16 colores|-96 x 96, 16 colores|
|-16 x 16, 256 colores|-48 x 48, 256 colores|-96 x 96, 256 colores|
|-16 x 16, monocromático|-48 x 48, monocromático|-96 x 96, monocromático|
|-32 x 32, 16 colores|-64 x 64, 16 colores||
|-32 x 32, 256 colores|-64 x 64, 256 colores||
|-32 x 32, monocromático|-64 x 64, monocromático||

> [!NOTE]
> Las imágenes ya existentes no se mostrará en esta lista.

El **personalizado** propiedad abre el **imagen personalizada** cuadro de diálogo en el que puede crear una nueva imagen con un tamaño personalizado y el número de colores.

El **imagen personalizada** cuadro de diálogo le permite crear una nueva imagen con un tamaño personalizado y el número de colores. Las siguientes propiedades que se incluyen son:

|Property|Descripción|
|---|---|
|**Width**|Proporciona un espacio para que escriba el ancho de la imagen personalizada en píxeles (1-512, límite de 2048).|
|**Height**|Proporciona un espacio para escribir el alto de la imagen personalizada en píxeles (1-512, límite de 2048).|
|**Colores**|Proporciona un espacio para elegir el número de colores para la imagen personalizada: 2, 16 o 256.|

Use la **abrir &lt;dispositivo&gt; imagen** cuadro de diálogo para abrir las imágenes de dispositivo en los proyectos de C++. Enumera las imágenes de dispositivo existentes en el recurso actual (imágenes que forman parte del recurso actual). Es la siguiente propiedad incluida:

|Property|Descripción|
|---|---|
|**Imágenes actuales**|Enumera las imágenes incluidas en el recurso. Seleccione el tipo de imagen que desea abrir.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Para crear un nuevo icono o cursor

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, haga clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [crear un nuevo archivo de Script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **Cursor** y elija **New**. Para los iconos, esta acción crea un recurso de icono con un 32 x 32, icono de 16 colores. Para los cursores, 32 x 32, se crea la imagen monocromática (2 colores).

   Si un signo más (**+**) aparece junto al tipo de recurso de imagen en el **Insertar recurso** cuadro de diálogo, significa que están disponibles plantillas de barra de herramientas. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **New**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Para agregar una imagen para otro dispositivo de presentación

1. En el **imagen** menú, seleccione **nueva imagen de dispositivo** (o haga clic en el **Editor de imágenes** panel y elija **nueva imagen de dispositivo** desde el menú contextual).

1. Seleccione el tipo de imagen que desea agregar. También puede seleccionar **personalizado** para crear un icono cuyo tamaño no está disponible en la lista predeterminada.

### <a name="to-copy-a-device-image"></a>Para copiar una imagen de dispositivo

1. En el **imagen** menú, seleccione **Abrir imagen de dispositivo** y elija una imagen de la lista de imágenes actual. Por ejemplo, elija la versión de 32 × 32, 16 colores de un icono.

1. Copie la imagen del icono muestra actualmente (**Ctrl**+**C**).

1. Abra otra imagen del icono en otro **Editor de imágenes** ventana. Por ejemplo, abra 16 x 16, versión 16 colores del icono.

1. Pegue la imagen del icono (**Ctrl**+**V**) desde una **Editor de imágenes** ventana a otra. Si va a pegar un tamaño mayor en un tamaño más pequeño, puede usar los controladores del icono para cambiar el tamaño de la imagen.

### <a name="to-delete-a-device-image"></a>Para eliminar una imagen de dispositivo

Mientras que la imagen del icono se muestra en el **imagen** editor, seleccione **Eliminar imagen de dispositivo** desde el **imagen** menú. Cuando se elimina la última imagen de icono en el recurso, también se elimina el recurso.

   > [!NOTE]
   > Cuando presiona el **SUPR** clave, las imágenes y los colores que se haya dibujado en un icono se eliminan, pero sigue siendo el icono; puede volver a diseñar, ahora. Si presiona **SUPR** por error, puede presionar **Ctrl**+**Z** deshacer la acción.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Para crear zonas transparentes o inversas en las imágenes de dispositivo

En el [editor de imágenes](../windows/image-editor-for-icons.md), la imagen inicial de icono o cursor tiene el atributo transparente. Aunque las imágenes de icono y cursor son rectangulares, muchos no aparecen, porque las partes de la imagen son transparentes; Muestra la imagen en la pantalla subyacente a través del icono o cursor. Cuando se arrastra un icono, partes de la imagen pueden aparecer en un color invertido. Crear este efecto estableciendo el color de la pantalla y el inverso en el [ventana colores](../windows/colors-window-image-editor-for-icons.md).

Los colores de pantalla e inversos se aplica a los iconos y cursores en la forma y la imagen derivada de color o asignación regiones inversas. Los colores indican las partes de la imagen que tienen esos atributos. Puede cambiar los colores que representan los atributos de color de la pantalla y color inverso en la edición. Estos cambios no afectan a la apariencia del icono o cursor en la aplicación.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la **Ayuda**, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Para crear zonas transparentes o inversas

1. En el **colores** ventana, seleccione el **Color de pantalla** selector o **Color inverso** selector.

1. Aplique la pantalla o el color inverso a la imagen mediante una herramienta de dibujo. Para obtener más información sobre herramientas de dibujo, consulte [mediante una herramienta de dibujo](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Para cambiar el color de pantalla o inverso

1. Seleccione el **Color de pantalla** selector o **Color inverso** selector.

1. Elija un color en el **colores** paleta en la **colores** ventana.

   Automáticamente se asigna el color complementario para el selector de otro.

   > [!TIP]
   > Si hace doble clic en el **Color de pantalla** o **Color inverso** selector, el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) aparece.

### <a name="use-the-256-color-palette"></a>Usa la paleta de 256 colores

Mediante el **imagen** editor, iconos y cursores pueden ser de tamaño grande (64 x 64) con una paleta de 256 colores para elegir. Después de crear el recurso, se selecciona un estilo de imagen de dispositivo.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Para crear un icono de 256 colores o cursor

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, haga clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **Cursor** y elija **New**.

1. En el **imagen** menú, seleccione **nueva imagen de dispositivo**.

1. Seleccione el estilo de imagen de 256 colores que desee.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Para elegir un color de la paleta de 256 colores para iconos grandes

Para dibujar con una selección de la paleta de 256 colores, deberá seleccionar los colores de la **colores** paleta en la [ventana colores](../windows/colors-window-image-editor-for-icons.md).

1. Seleccione el icono o cursor grande o cree un nuevo icono o cursor grande.

1. Elija un color de los 256 colores mostrados en la **colores** paleta en la **colores** ventana.

   El color seleccionado se convertirá en el color actual en el **colores** paleta en la **colores** ventana.

   > [!NOTE]
   > La paleta inicial que se usa para imágenes de 256 colores coincide con la paleta devuelta por la `CreateHalftonePalette` API de Windows. Todos los iconos previstos para el shell de Windows deben usar esta paleta para impedir el parpadeo durante la realización de la paleta.

### <a name="set-a-cursor39s-hot-spot"></a>Para establecer un cursor&#39;s crucial.

La zona activa de un cursor es el punto en que Windows hace referencia en el seguimiento de la posición del cursor. De forma predeterminada, la zona activa se establece en la esquina superior izquierda del cursor (coordenadas 0,0). El **Hotspot** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window) muestra las coordenadas de la zona activa.

#### <a name="to-set-a-cursors-hot-spot"></a>Establecer zona activa del cursor

1. En el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md), elija el **establecer zona activa** herramienta.

1. Seleccione el píxel que desea asignar como zona activa del cursor.

   El **Hotspot** propiedad en el **propiedades** ventana muestra las nuevas coordenadas.

   > [!TIP]
   > Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

## <a name="saving-bitmaps-as-gifs-or-jpegs"></a>Guardar un mapa de bits con formato GIF o JPEG

Cuando se crea un mapa de bits, se crea la imagen en formato de mapa de bits (.bmp). Sin embargo, puede guardar la imagen como GIF o JPEG o en otros formatos de gráficos.

> [!NOTE]
> Este proceso no se aplica a los iconos y cursores.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Para crear y guardar un mapa de bits como un archivo .gif o .jpeg

1. Desde el **archivo** menú, elija **abierto**, a continuación, seleccione **archivo**.

1. En el **cuadro de diálogo nuevo archivo**, elija el **Visual C++** carpeta, a continuación, seleccione **el archivo de mapa de bits (.bmp)** en el **plantillas** cuadro y seleccione  **Abra**.

   El mapa de bits se abre en el **imagen** editor.

1. Realizar cambios en el nuevo mapa de bits, según sea necesario.

1. Con el mapa de bits sigue abierto en el **imagen** editor, elija **guardar *filename*.bmp como** en el **archivo** menú.

1. En el **Guardar archivo como** diálogo cuadro, escriba el nombre que desea dar al archivo y la extensión que denota el formato de archivo que desee en el **nombre de archivo** cuadro. Por ejemplo, *miarchivo.gif*.

   > [!NOTE]
   > Debe crear o abrir el mapa de bits fuera de su proyecto para poder guardarlo en otro formato de archivo. Si crea o abrirlo en el proyecto, el **Guardar como** comando dejará de estar disponible. Para obtener más información, consulte [ver recursos en un archivo de Script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Seleccione **Guardar**.

## <a name="converting-an-image-from-one-format-to-another"></a>Convertir una imagen de un formato en otro

Puede abrir imágenes GIF o JPEG en la **imagen** editor y guardarlos como mapas de bits. Además, puede abrir un archivo de mapa de bits y guardarla como JPEG o GIF. Trabajar con las imágenes no necesitan ser parte de un proyecto para editarlo en el entorno de desarrollo (vea [edición de imágenes independientes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

### <a name="to-convert-an-image-from-one-format-to-another"></a>Para convertir una imagen de un formato a otro

1. Abra la imagen en el **imagen** editor.

1. Desde el **archivo** menú, elija **guardar *filename* como**.

1. En el **Guardar archivo como** cuadro de diálogo el **nombre de archivo** , escriba el nombre de archivo y la extensión que denota el formato que desee.

1. Seleccione **Guardar**.

## <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Para agregar un nuevo recurso de imagen a un proyecto de C++ no administrado

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, puede hacer simplemente clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione el tipo de recurso de imagen que le gustaría crear (**mapa de bits**, por ejemplo), a continuación, elija **New**.

   Si un signo más (**+**) aparece junto al tipo de recurso de imagen en el **Insertar recurso** cuadro de diálogo, significa que están disponibles plantillas de barra de herramientas. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **New**.

## <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Para agregar un nuevo recurso de imagen a un proyecto en un lenguaje de programación de .NET

1. En **el Explorador de soluciones**, haga clic en la carpeta del proyecto (por ejemplo, `WindowsApplication1`).

1. En el menú contextual, seleccione **agregar**, a continuación, elija **Agregar nuevo elemento**.

1. En el **categorías** panel, expanda el **elementos de proyecto Local** carpeta, a continuación, elija **recursos**.

1. En el **plantillas** panel, elija el tipo de recurso que le gustaría agregar a su proyecto.

   El recurso se agrega al proyecto en **el Explorador de soluciones** y el recurso se abrirá en el [editor de imágenes](../windows/image-editor-for-icons.md). Ahora puede usar todas las herramientas disponibles en el editor de imágenes para modificar la imagen. Para obtener más información sobre cómo agregar imágenes a un proyecto administrado, consulte [cargar una imagen en tiempo de diseño](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

   > [!NOTE]
   > Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados. Para obtener más información, consulte [crear archivos de recursos](/dotnet/framework/resources/creating-resource-files-for-desktop-apps) en el *Guía del desarrollador de .NET Framework*.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Conversión de mapas de bits en barras de herramientas](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creación de nuevas barras de herramientas](../windows/creating-new-toolbars.md)<br/>
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Imagen (menú)](../windows/image-menu-image-editor-for-icons.md)<br/>
[Iconos](/windows/desktop/menurc/icons)<br/>
[Cursores](/windows/desktop/menurc/cursors)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
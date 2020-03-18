---
title: 'Cómo: crear un icono u otra imagen'
ms.date: 02/15/2019
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
ms.openlocfilehash: 046b7e0070d95f5d17b3240884db76533f1c6ccd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443917"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Cómo: crear un icono u otra imagen

Puede crear una nueva imagen, mapa de bits, icono, cursor o barra de herramientas y, a continuación, usar el **Editor de imágenes** para personalizar su apariencia. También puede crear un nuevo mapa de bits a partir de una [plantilla de recursos](../windows/how-to-use-resource-templates.md).

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Iconos y cursores: recursos de imagen para dispositivos de presentación

Los iconos y cursores son recursos gráficos que pueden contener varias imágenes de diferentes tamaños y combinaciones de colores para distintos tipos de dispositivos de pantalla. Un cursor también tiene una zona activa, la ubicación que Windows usa para realizar un seguimiento de su posición. Tanto los iconos como los cursores se crean y se editan mediante el **Editor de imágenes**, al igual que los mapas de bits y otras imágenes.

Al crear un nuevo icono o cursor, el **Editor de imágenes** crea primero una imagen de un tipo estándar. La imagen se rellena inicialmente con el color de la pantalla (transparente). Si la imagen es un cursor, la zona activa es inicialmente la esquina superior izquierda con las coordenadas `0,0`.

De forma predeterminada, el **Editor de imágenes** admite la creación de imágenes adicionales para los dispositivos que se muestran en la tabla siguiente. Puede crear imágenes para otros dispositivos escribiendo parámetros de ancho, alto y número de colores en el cuadro de diálogo **imagen personalizada** .

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

Cuando se crea un nuevo recurso de icono o de cursor, el **Editor de imágenes** crea primero una imagen con un estilo específico (32 × 32, 16 colores para los iconos y 32 × 32, monocromo para los cursores). Después, puede Agregar imágenes de diferentes tamaños y estilos al icono o cursor inicial y editar cada imagen adicional, según sea necesario, para los distintos dispositivos de pantalla. También puede editar una imagen mediante una operación de cortar y pegar desde un tipo de imagen existente o desde un mapa de bits creado en un programa de gráficos.

Al abrir el icono o el recurso de cursor en el [Editor de imágenes](../windows/image-editor-for-icons.md), se abre de forma predeterminada la imagen que coincide más estrechamente con el dispositivo de pantalla actual.

> [!NOTE]
> Si el proyecto aún no contiene un archivo. rc, consulte [crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

El cuadro de diálogo **nuevo &lt;dispositivo&gt; tipo de imagen** permite crear una nueva imagen de dispositivo de un tipo especificado. Para abrir el cuadro de diálogo **nuevo \<dispositivo > imagen** , vaya a **imagen** de menú > **nuevo tipo de imagen**. Las siguientes propiedades son **tipo de imagen de destino** y **personalizado**.

La propiedad **tipo de imagen de destino** muestra los tipos de imagen disponibles donde se selecciona el tipo de imagen que desea abrir:

||||
|-|-|-|
|-16 x 16, 16 colores|-48 x 48, 16 colores|-96 x 96, 16 colores|
|-16 x 16, 256 colores|-48 x 48, 256 colores|-96 x 96, 256 colores|
|-16 x 16, monocromo|-48 x 48, monocromo|-96 x 96, monocromo|
|-32 x 32, 16 colores|-64 x 64, 16 colores||
|-32 x 32, 256 colores|-64 x 64, 256 colores||
|-32 x 32, monocromo|-64 x 64, monocromo||

> [!NOTE]
> Las imágenes existentes no se mostrarán en esta lista.

La propiedad **personalizada** abre el cuadro de diálogo **imagen personalizada** en el que puede crear una nueva imagen con un tamaño personalizado y un número de colores.

El cuadro de diálogo **imagen personalizada** permite crear una nueva imagen con un tamaño personalizado y un número de colores. Las siguientes propiedades se incluyen:

|Propiedad|Descripción|
|---|---|
|**Width**|Proporciona un espacio para que escriba el ancho de la imagen personalizada en píxeles (1-512, límite de 2048).|
|**Height**|Proporciona un espacio para que escriba el alto de la imagen personalizada en píxeles (1-512, límite de 2048).|
|**Colores**|Proporciona un espacio para que elija el número de colores de la imagen personalizada: 2, 16 o 256.|

Use el cuadro de diálogo **abrir &lt;dispositivo&gt; imagen** para abrir imágenes de C++ dispositivo en proyectos. Muestra las imágenes de dispositivo existentes en el recurso actual (imágenes que forman parte del recurso actual). La siguiente propiedad incluida es:

|Propiedad|Descripción|
|---|---|
|**Imágenes actuales**|Muestra las imágenes incluidas en el recurso. Seleccione el tipo de imagen que desea abrir.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Para crear un nuevo icono o cursor

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic con el botón derecho en el archivo *. RC* y elija **Insertar recurso**. Si ya tiene un recurso de imagen en el archivo *. RC* , como un cursor, puede hacer clic con el botón secundario en la carpeta **cursor** y seleccionar **Insertar cursor**.

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **cursor** y elija **nuevo**. En el caso de los iconos, esta acción crea un recurso de icono con un icono de 32 × 32 y 16 colores. En el caso de los cursores, se crea una imagen monocromática de 32 × 32 (2 colores).

   Si aparece un signo más ( **+** ) junto al tipo de recurso de imagen en el cuadro de diálogo **Insertar recurso** , significa que las plantillas de barra de herramientas están disponibles. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **nuevo**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Para agregar una imagen para un dispositivo de pantalla diferente

1. Vaya a la **imagen** de menú > **nueva imagen de dispositivo**o haga clic con el botón derecho en el panel del **Editor de imágenes** y elija **nueva imagen de dispositivo**.

1. Seleccione el tipo de imagen que desea agregar. También puede seleccionar **personalizado** para crear un icono cuyo tamaño no esté disponible en la lista predeterminada.

### <a name="to-copy-a-device-image"></a>Para copiar una imagen de dispositivo

1. Vaya a la **imagen** de menú > **abrir imagen de dispositivo** y elija una imagen en la lista imágenes actuales. Por ejemplo, elija la versión 32 × 32, de 16 colores de un icono.

1. Copie la imagen del icono que se muestra actualmente (**Ctrl**+**C**).

1. Abra una imagen diferente del icono en otra ventana del **Editor de imágenes** . Por ejemplo, abra la versión de 16 × 16 y 16 colores del icono.

1. Pegue la imagen de icono (**Ctrl**+**V**) de una ventana del **Editor de imágenes** en la otra. Si va a pegar un tamaño mayor en un tamaño más pequeño, puede usar los controladores de icono para cambiar el tamaño de la imagen.

### <a name="to-delete-a-device-image"></a>Para eliminar una imagen de dispositivo

Mientras se muestra la imagen de icono en el **Editor de imágenes**, vaya a **imagen** de menú > **Eliminar imagen de dispositivo**. Al eliminar la última imagen de icono en el recurso, también se elimina el recurso.

> [!NOTE]
> Al presionar la tecla **Supr** , las imágenes y los colores que ha dibujado en un icono se eliminan, pero el icono permanece y ahora puede rediseñarlo. Si presiona **Supr** por error, presione **Ctrl**+**Z** para deshacer la acción.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Para crear regiones transparentes o inversas en las imágenes de dispositivo

En el [Editor de imágenes](../windows/image-editor-for-icons.md), el icono inicial o la imagen del cursor tienen un atributo transparente. Aunque las imágenes de icono y de cursor son rectangulares, muchas no aparecen, ya que las partes de la imagen son transparentes y la imagen subyacente en la pantalla se muestra a través del icono o el cursor. Al arrastrar un icono, pueden aparecer partes de la imagen en un color invertido. Para crear este efecto, establezca el color de la pantalla y el color inverso en la [ventana colores](../windows/colors-window-image-editor-for-icons.md).

Los colores de pantalla e inversos que se aplican a los iconos y cursores de forma y color de la imagen derivada o de la asignación de regiones inversas. Los colores indican partes de la imagen que tienen esos atributos. Puede cambiar los colores que representan los atributos de color de pantalla e inverso en la edición. Estos cambios no afectan a la apariencia del icono o del cursor en la aplicación.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la **Ayuda**, en función de los valores de configuración o de edición activos. Para cambiar la configuración, vaya a **herramientas** de menú > **importar y exportar configuraciones**. Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Para crear regiones transparentes o inversas

1. En la ventana **colores** , elija el color de la **pantalla** selector o el **color inverso**.

1. Aplique la pantalla o el color inverso a la imagen mediante una herramienta de dibujo. Para obtener más información sobre las herramientas de dibujo, vea [usar una herramienta de dibujo](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Para cambiar la pantalla o el color inverso

1. Seleccione el selector **de colores de pantalla** o el selector **de color inverso** .

1. Elija un color de la paleta **colores** en la ventana **colores** .

   El color complementario se asigna automáticamente para el otro selector.

   > [!TIP]
   > Si hace doble clic en el selector de colores de **pantalla** o de color **inverso** , aparece el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) .

### <a name="use-the-256-color-palette"></a>Usar la paleta de colores 256

Con el **Editor de imágenes**, los iconos y los cursores pueden tener un tamaño grande (64 × 64) con una paleta de 256 colores para elegir. Después de crear el recurso, se selecciona un estilo de imagen de dispositivo.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Para crear un icono o un cursor de 256 colores

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic con el botón derecho en el archivo *. RC* y elija **Insertar recurso**. Si ya tiene un recurso de imagen en el archivo *. RC* , como un cursor, puede hacer clic con el botón secundario en la carpeta **cursor** y seleccionar **Insertar cursor**.

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **cursor** y elija **nuevo**.

1. Vaya a la **imagen** de menú > **imagen de dispositivo nuevo** y seleccione el estilo de imagen de 256 colores que quiera.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Para elegir un color de la paleta de 256 colores para iconos grandes

Para dibujar con una selección de la paleta de 256 colores, debe seleccionar los colores de la paleta de **colores** en la [ventana colores](../windows/colors-window-image-editor-for-icons.md).

1. Seleccione el icono o el cursor grande o cree un nuevo icono o cursor grande.

1. Elija un color de los colores 256 mostrados en la paleta de **colores** de la ventana **colores** .

   El color seleccionado se convertirá en el color actual de la paleta de **colores** de la ventana **colores** .

   > [!NOTE]
   > La paleta inicial utilizada para las imágenes de 256 colores coincide con la paleta devuelta por el `CreateHalftonePalette` API de Windows. Todos los iconos destinados al shell de Windows deben usar esta paleta para evitar el parpadeo durante la realización de la paleta.

### <a name="to-set-a-cursors-hot-spot"></a>Para establecer la zona activa de un cursor

La zona activa de un cursor es el punto al que hace referencia Windows para realizar el seguimiento de la posición del cursor. De forma predeterminada, la zona activa se establece en la esquina superior izquierda del cursor con las coordenadas `0,0`. La propiedad **HotSpot** del [ventana Propiedades](/visualstudio/ide/reference/properties-window) muestra las coordenadas de la zona activa.

1. En la [barra de herramientas del editor de imágenes](../windows/toolbar-image-editor-for-icons.md), elija la herramienta **establecer zona activa** .

1. Seleccione el píxel que desea asignar como zona activa del cursor.

   La propiedad **HotSpot** de la ventana **propiedades** muestra las nuevas coordenadas.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Para crear y guardar un mapa de bits como archivo. gif o. JPEG

Cuando se crea un mapa de bits, la imagen se crea en formato de mapa de bits (. bmp). Sin embargo, puede guardar la imagen como GIF o JPEG o en otros formatos de gráficos.

> [!NOTE]
> Este proceso no se aplica a los iconos y cursores.

1. Vaya a **archivo** de menú > **abrir**y seleccione **archivo**.

1. En el **cuadro de diálogo nuevo archivo**, elija la carpeta **Visual C++**  y, a continuación, seleccione **archivo de mapa de bits (. bmp)** en el cuadro **plantillas** y seleccione **abrir**.

   El mapa de bits se abre en el **Editor de imágenes**.

1. Realice cambios en el nuevo mapa de bits según sea necesario.

1. Con el mapa de bits todavía abierto en el **Editor de imágenes**, vaya a **archivo** de menú > **Guardar *filename*. bmp como**.

1. En el cuadro de diálogo **Guardar archivo como** , escriba el nombre que desea asignar al archivo y la extensión que indica el formato de archivo que desea incluir en el cuadro **nombre de archivo** . Por ejemplo, *archivo. gif*.

   > [!NOTE]
   > Debe crear o abrir el mapa de bits fuera del proyecto para guardarlo como otro formato de archivo. Si lo crea o abre en el proyecto, el comando **Guardar como** no estará disponible. Para obtener más información, vea [ver recursos en un archivo de script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Seleccione **Guardar**.

### <a name="to-convert-an-image-from-one-format-to-another"></a>Para convertir una imagen de un formato a otro

Puede abrir imágenes GIF o JPEG en el **Editor de imágenes** y guardarlas como mapas de bits. Además, puede abrir un archivo de mapa de bits y guardarlo como GIF o JPEG. Las imágenes con las que trabaja no deben formar parte de un proyecto para su edición en el entorno de desarrollo (consulte [edición de imágenes independientes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

1. Abra la imagen en el **Editor de imágenes**.

1. Vaya a **archivo** de menú > **Guardar *nombre* de archivo como**.

1. En el cuadro de diálogo **Guardar archivo como** , en el cuadro **nombre de archivo** , escriba el nombre de archivo y la extensión que indique el formato que desee.

1. Seleccione **Guardar**.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Para agregar un nuevo recurso de imagen a un C++ proyecto no administrado

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic con el botón derecho en el archivo *. RC* y elija **Insertar recurso**. Si ya tiene un recurso de imagen en el archivo *. RC* , como un cursor, simplemente puede hacer clic con el botón derecho en la carpeta **cursor** y seleccionar **Insertar cursor**.

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione el tipo de recurso de imagen que desea crear (por ejemplo,**mapa de bits**) y, a continuación, elija **nuevo**.

   Si aparece un signo más ( **+** ) junto al tipo de recurso de imagen en el cuadro de diálogo **Insertar recurso** , significa que las plantillas de barra de herramientas están disponibles. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **nuevo**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Para agregar un nuevo recurso de imagen a un proyecto en un lenguaje de programación .NET

1. En **Explorador de soluciones**, haga clic con el botón secundario en la carpeta del proyecto (por ejemplo, *WindowsApplication1*).

1. En el menú contextual, seleccione **Agregar**y, a continuación, elija **Agregar nuevo elemento**.

1. En el panel **categorías** , expanda la carpeta **elementos de proyecto locales** y, a continuación, elija **recursos**.

1. En el panel **plantillas** , elija el tipo de recurso que desee agregar al proyecto.

   El recurso se agrega al proyecto en **Explorador de soluciones** y el recurso se abre en el [Editor de imágenes](../windows/image-editor-for-icons.md). Ahora puede usar todas las herramientas disponibles en el **Editor de imágenes** para modificar la imagen. Para obtener más información sobre cómo agregar imágenes a un proyecto administrado, vea [cargar una imagen en tiempo de diseño](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

## <a name="requirements"></a>Requisitos

None

## <a name="see-also"></a>Consulte también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: editar una imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Cómo: usar una herramienta de dibujo](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Cómo: trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->
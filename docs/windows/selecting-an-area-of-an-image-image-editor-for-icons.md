---
title: Procedimiento Editar una imagen
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 849da0d14987a057d39d5f9531e97545b3d4b8cf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033299"
---
# <a name="how-to-edit-an-image"></a>Procedimiento Editar una imagen

Puede usar herramientas de selección para definir un área de una imagen que desee cortar, copiar, borrar, cambiar el tamaño, invertir o mover. Con el **rectángulo de selección** herramienta puede definir y seleccionar una región rectangular de la imagen. Con el **selección Irregular** herramienta que puede dibujar un contorno del área que desea seleccionar para la operación de cortar, copiar u otra operación a mano alzada.

> [!NOTE]
> Consulte la **rectángulo de selección** y **selección Irregular** herramientas en la imagen en [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o ver la información sobre herramientas asociada con cada botón en el **Editor de imágenes** barra de herramientas.

También puede crear un pincel personalizado de una selección. Para obtener más información, consulte [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Procedimientos

Para editar una imagen, consulte Cómo:

### <a name="to-select-an-image"></a>Para seleccionar una imagen

1. Use la **Editor de imágenes** barra de herramientas o vaya al menú **imagen** > **herramientas** y elija la herramienta de selección que desee.

1. Mover el punto de inserción a una esquina del área de imagen que desea seleccionar. Cruz aparecen cuando el punto de inserción está sobre la imagen.

1. Arrastre el punto de inserción a la esquina opuesta del área que desea seleccionar. Un rectángulo muestra los píxeles que se seleccionará. Todos los píxeles dentro del rectángulo, las de rectángulo, incluidas se incluyen en la selección.

1. Suelte el botón del mouse. El borde de selección rodea el área seleccionada.

#### <a name="to-select-an-entire-image"></a>Para seleccionar una imagen completa

Seleccione la imagen fuera de la selección actual. El borde de selección cambia el foco y abarca toda la imagen una vez más.

### <a name="to-edit-parts-of-an-image"></a>Para modificar partes de una imagen

Puede realizar las operaciones de edición estándares, cortar, copiar, borrar y mover, en un [selección](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), si la selección es la imagen completa o solamente una parte de ella. Dado que el **Editor de imágenes** usa el **Portapapeles de Windows**, puede transferir imágenes entre el **Editor de imágenes** y otras aplicaciones para Windows.

Además, puede cambiar la selección, si incluye toda la imagen o sólo una parte.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Para cortar la selección actual y colocarlo en el Portapapeles

Vaya al menú **editar** > **cortar**.

#### <a name="to-copy-the-selection"></a>Para copiar la selección

1. Coloque el puntero dentro del borde de selección o en cualquier lugar en el mismo, excepto los controladores de tamaño.

1. Mantenga presionada la **Ctrl** mientras arrastra la selección a una nueva ubicación de la clave. No se modifica el área de la selección original.

1. Para copiar la selección en la imagen en su ubicación actual, seleccione fuera del cursor de selección.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Para pegar el contenido del Portapapeles en una imagen

1. Vaya al menú **editar** > **pegar**.

   El contenido del Portapapeles, rodeado por el borde de selección, aparece en la esquina superior izquierda del panel.

1. Coloque el puntero en el borde de selección y arrástrela hasta la ubicación deseada en la imagen.

1. Para fijar la imagen en su nueva ubicación, seleccione fuera del borde de selección.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Para eliminar la selección actual sin moverlo en el Portapapeles

Vaya al menú **editar** > **eliminar**.

   El área de la selección original se rellena con el color de fondo actual.

> [!NOTE]
> Puede tener acceso a la **cortar**, **copia**, **pegar**, y **eliminar** comandos con el botón secundario en el **devistaderecursos** ventana.

#### <a name="to-move-the-selection"></a>Para mover la selección

1. Coloque el puntero dentro del borde de selección o en cualquier lugar en el mismo, excepto los controladores de tamaño.

1. Arrastre la selección a su nueva ubicación.

1. Para fijar la selección en la imagen en su nueva ubicación, seleccione fuera del borde de selección.

Para obtener más información sobre cómo dibujar con una selección, consulte [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Para voltear una imagen

Puede girar o voltear una imagen para crear una imagen reflejada del original, se invierte la imagen o girar la imagen a la derecha 90 grados a la vez.

- La imagen se voltea horizontalmente (imagen reflejada), vaya al menú **imagen** > **Voltear horizontalmente**.

- La imagen se voltea verticalmente (colocar al revés), vaya al menú **imagen** > **Voltear verticalmente**.

- Para girar la imagen 90 grados, vaya al menú **imagen** > **Girar 90 grados**.

   > [!NOTE]
   > También puede usar el [teclas de aceleración (método abreviado)](../windows/accelerator-keys-image-editor-for-icons.md) para estos comandos u obtener acceso a los comandos en el menú contextual (seleccione fuera de la imagen en el **Editor de imágenes**).

### <a name="to-resize-an-image"></a>Para cambiar el tamaño de una imagen

El comportamiento de la **Editor de imágenes** mientras el cambio de tamaño una imagen depende de si ha [seleccionado](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) la imagen completa o sólo una parte del mismo.

Cuando la selección incluye sólo una parte de la imagen, el **Editor de imágenes** reduce la selección, eliminación de filas o columnas de píxeles y rellenando las vacantes regiones con el color de fondo actual. También puede ampliar la selección al duplicar filas o columnas de píxeles.

Cuando la selección incluye toda la imagen, el **Editor de imágenes** bien reduce y expande la imagen, o se recorta y lo amplía.

Hay dos mecanismos para cambiar el tamaño de una imagen: los controladores de tamaño y la [ventana propiedades](/visualstudio/ide/reference/properties-window). Arrastre los controladores de tamaño para cambiar el tamaño de todo o parte de una imagen. Ajuste de tamaño que se pueden arrastrar son sólidos. No puede arrastrar cuadros huecos. Use la **propiedades** ventana para cambiar el tamaño de toda la imagen solo, no es una parte seleccionada.

![Controladores en un mapa de bits de tamaño](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Controladores de tamaño

> [!NOTE]
> Si tiene la **cuadrícula de mosaico** opción seleccionada en el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md), a continuación, cambiar el tamaño se ajusta a la siguiente línea de cuadrícula de mosaico. Si solo el **cuadrícula de píxeles** opción está seleccionada (el valor predeterminado), el cambio de tamaño se ajusta a la siguiente píxel disponible.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Para cambiar el tamaño de una imagen completa mediante la ventana Propiedades

1. Abra la imagen cuyas propiedades desea cambiar.

1. En el **ancho** y **alto** cuadros en el [ventana propiedades](/visualstudio/ide/reference/properties-window), escriba las dimensiones que desee.

   Si va a aumentar el tamaño de la imagen, el **Editor de imágenes** amplía la imagen a la derecha, hacia abajo, o ambos y rellena la nueva región con el color de fondo actual. La imagen no quede estirada.

   Si reduce el tamaño de la imagen, el **Editor de imágenes** recorta la imagen en el borde derecho o inferior, o ambos.

   > [!NOTE]
   > Puede usar el **ancho** y **alto** propiedades para cambiar el tamaño de la imagen completa no para cambiar el tamaño de una selección parcial.

#### <a name="to-crop-or-extend-an-entire-image"></a>Para recortar o ampliar una imagen completa

1. Seleccione toda la imagen.

   Si parte de la imagen está seleccionado actualmente y que desea seleccionar toda la imagen, seleccione cualquier parte de la imagen fuera del borde de selección actual.

1. Arrastre un controlador de tamaño hasta que la imagen es el tamaño correcto.

Normalmente, el **Editor de imágenes** recorta o amplía una imagen cuando cambia el tamaño al mover un controlador de tamaño. Si mantiene presionada la **MAYÚS** clave como mover un controlador de tamaño, el **Editor de imágenes** reduce o expande la imagen.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Para comprimir o ajustar una imagen completa

1. Seleccione toda la imagen.

   Si una parte de la imagen está seleccionada actualmente y que desea seleccionar toda la imagen, seleccione cualquier parte de la imagen fuera del borde de selección actual.

1. Mantenga presionada la **MAYÚS** clave y arrastre un controlador de tamaño hasta que la imagen es el tamaño correcto.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Para comprimir o expandir parte de una imagen

1. Seleccione la parte de la imagen que desea cambiar el tamaño. Para obtener más información, consulte [seleccionar un área de la imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Arrastre uno de los controladores de tamaño hasta que la selección es el tamaño correcto.

### <a name="to-edit-an-image-outside-of-a-project"></a>Para editar una imagen fuera de un proyecto

Puede abrir y editar imágenes en el entorno de desarrollo, como haría en cualquier aplicación de gráficos, por ejemplo abriendo un mapa de bits para edición independiente. Las imágenes con que se trabaja no deben formar parte de un proyecto de Visual Studio.

1. Vaya al menú **archivo** > **abierto**.

1. En el **archivos de tipo** cuadro, seleccione **todos los archivos**.

1. Busque y abra la imagen que desea editar.

### <a name="to-change-image-properties"></a>Para cambiar las propiedades de imagen

Puede establecer o modificar las propiedades de una imagen mediante la [ventana propiedades](/visualstudio/ide/reference/properties-window).

1. Abra la imagen en el **Editor de imágenes**.

1. En el **propiedades** ventana, cambie cualquiera o todas las propiedades para la imagen.

   |Propiedad|Descripción|
   |--------------|-----------------|
   |**Colores**|Especifica la combinación de colores para la imagen. Seleccione **monocromático**, **16**, o **256**, o **Color verdadero**.<br/><br/>Si ya ha dibujado la imagen con una paleta de colores de 16, si selecciona **monocromático** hace que las sustituciones de blanco y negro para los colores en la imagen. No se mantiene siempre contraste: por ejemplo, las áreas adyacentes de color rojo y verde se ambos convierten a negro.|
   |**Nombre de archivo**|Especifica el nombre del archivo de imagen.<br/><br/>De forma predeterminada, Visual Studio asigna un nombre de archivo base creado mediante la eliminación de los primeros cuatro caracteres ("IDB_") desde el identificador de recursos predeterminado (IDB_BITMAP1) y agregando la extensión adecuada. El nombre de archivo para la imagen en este ejemplo sería *BITMAP1.bmp*. Puede cambiar el nombre *este nombre a MIBITMAP1.bmp*.|
   |**Height**|Establece el alto de la imagen (en píxeles). El valor predeterminado es 48.<br/><br/>La imagen se recorta o se agrega espacio en blanco debajo de la imagen existente.|
   |**ID**|Establece el identificador de recursos.<br/><br/>Para una imagen, Microsoft Visual Studio, de forma predeterminada, asigna el siguiente identificador disponible en una serie: IDB_BITMAP1, IDB_BITMAP2 y así sucesivamente. Se usan nombres similares para iconos y cursores.|
   |**Palette**|Cambia las propiedades de color.<br/><br/>Haga doble clic para seleccionar un color y mostrar el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Definir el color escribiendo los valores RGB o HSL en los cuadros de texto correspondientes.|
   |**SaveCompressed**|Indica si la imagen está en un formato comprimido. Esta propiedad es de sólo lectura.<br/><br/>Visual Studio no le permite guardar las imágenes en un formato comprimido, por lo que las imágenes creadas en Visual Studio, esta propiedad será **False**. Si abre una imagen comprimida (creada en otro programa) en Visual Studio, esta propiedad será **True**. Si guarda una imagen comprimida con Visual Studio, se descomprimen y esta propiedad se restablecerá a **False**.|
   |**Width**|Establece el ancho de la imagen (en píxeles). El valor predeterminado para los mapas de bits es 48.<br/><br/>La imagen se recorta o espacio en blanco se agrega a la derecha de la imagen existente.|

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: Creación de un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Cómo: Uso de una herramienta de dibujo](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Cómo: Trabajo con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
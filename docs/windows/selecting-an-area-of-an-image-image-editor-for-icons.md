---
title: 'Cómo: editar una imagen'
ms.date: 02/15/2019
f1_keywords:
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
ms.openlocfilehash: 6d973ad444f719b905af5a33e47ef28f4895111f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447290"
---
# <a name="how-to-edit-an-image"></a>Cómo: editar una imagen

Puede usar las herramientas de selección para definir un área de una imagen que desee cortar, copiar, borrar, cambiar de tamaño, invertir o desplace. Con la herramienta **selección de rectángulo** puede definir y seleccionar una región rectangular de la imagen. Con la herramienta **selección irregular** puede dibujar un contorno de FreeHand del área que desea seleccionar para cortar, copiar u otra operación.

> [!NOTE]
> Vea las herramientas **selección de rectángulo** y **selección irregular** que aparecen en la [barra de herramientas del editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o vea la información sobre herramientas asociada a cada botón en la barra de herramientas del editor de **imágenes** .

También puede crear un pincel personalizado a partir de una selección. Para obtener más información, vea [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Procedimientos

Para editar una imagen, consulte Cómo:

### <a name="to-select-an-image"></a>Para seleccionar una imagen

1. Use la barra de herramientas del **Editor de imágenes** o vaya a la **imagen** de menú > **herramientas** y elija la herramienta de selección que desee.

1. Mueva el punto de inserción a una esquina del área de la imagen que desea seleccionar. Los cruces aparecen cuando el punto de inserción está sobre la imagen.

1. Arrastre el punto de inserción hasta la esquina opuesta del área que desea seleccionar. Un rectángulo muestra qué píxeles se seleccionarán. En la selección se incluyen todos los píxeles del rectángulo, incluidos los del rectángulo.

1. Suelte el botón del mouse (ratón). El borde de selección incluye el área seleccionada.

#### <a name="to-select-an-entire-image"></a>Para seleccionar una imagen completa

Seleccione la imagen fuera de la selección actual. El borde de selección cambia el foco y abarca toda la imagen una vez más.

### <a name="to-edit-parts-of-an-image"></a>Para editar partes de una imagen

Puede realizar operaciones de edición estándar (cortar, copiar, borrar y mover) en una [selección](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), independientemente de que la selección sea la imagen completa o solo una parte de ella. Dado que el **Editor de imágenes** usa el **portapapeles de Windows**, puede transferir imágenes entre el editor de **imágenes** y otras aplicaciones para Windows.

Además, puede cambiar el tamaño de la selección, tanto si incluye la imagen completa como si solo una parte.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Para cortar la selección actual y moverla al portapapeles

Vaya a menú **editar** > **cortar**.

#### <a name="to-copy-the-selection"></a>Para copiar la selección

1. Coloque el puntero en el borde de la selección o en cualquier lugar del mismo, excepto los controladores de tamaño.

1. Mantenga presionada la tecla **Ctrl** mientras arrastra la selección a una nueva ubicación. El área de la selección original no cambia.

1. Para copiar la selección en la imagen en su ubicación actual, seleccione fuera del cursor de selección.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Para pegar el contenido del portapapeles en una imagen

1. Vaya a menú **editar** > **pegar**.

   El contenido del portapapeles, rodeado del borde de la selección, aparece en la esquina superior izquierda del panel.

1. Coloque el puntero en el borde de selección y arrastre la imagen hasta la ubicación deseada en la imagen.

1. Para delimitar la imagen en su nueva ubicación, seleccione fuera del borde de selección.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Para eliminar la selección actual sin moverla al portapapeles

Vaya a menú **editar** > **eliminar**.

   El área original de la selección se rellena con el color de fondo actual.

> [!NOTE]
> Puede tener acceso a los comandos **cortar**, **copiar**, **pegar**y **eliminar** haciendo clic con el botón secundario en la ventana **vista de recursos** .

#### <a name="to-move-the-selection"></a>Para deshacer la selección

1. Coloque el puntero en el borde de la selección o en cualquier lugar del mismo, excepto los controladores de tamaño.

1. Arrastre la selección a su nueva ubicación.

1. Para delimitar la selección de la imagen en su nueva ubicación, seleccione fuera del borde de selección.

Para obtener más información sobre cómo dibujar con una selección, vea [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Para voltear una imagen

Puede voltear o girar una imagen para crear una imagen reflejada del original, girar la imagen hacia abajo o girar la imagen a la derecha 90 grados a la vez.

- Para voltear la imagen horizontalmente (imagen reflejada), vaya a **imagen** de menú > **Voltear horizontalmente**.

- Para voltear la imagen verticalmente (desactivar), vaya a **imagen** de menú > **voltear verticalmente**.

- Para girar la imagen 90 grados, vaya a la **imagen** de menú > **girar 90 grados**.

   > [!NOTE]
   > También puede usar las [teclas de aceleración (Shortcut)](../windows/accelerator-keys-image-editor-for-icons.md) de estos comandos o tener acceso a los comandos desde el menú contextual (seleccione fuera de la imagen en el **Editor de imágenes**).

### <a name="to-resize-an-image"></a>Para cambiar el tamaño de una imagen

El comportamiento del **Editor de imágenes** al cambiar el tamaño de una imagen depende de si ha [seleccionado](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) la imagen completa o simplemente parte de ella.

Cuando la selección incluye solo parte de la imagen, el **Editor de imágenes** reduce la selección eliminando filas o columnas de píxeles y rellenando las regiones vacías con el color de fondo actual. También puede ampliar la selección duplicando filas o columnas de píxeles.

Cuando la selección incluye la imagen completa, el **Editor de imágenes** reduce y estira la imagen, o la recorta y la amplía.

Hay dos mecanismos para cambiar el tamaño de una imagen: los controladores de tamaño y el [ventana Propiedades](/visualstudio/ide/reference/properties-window). Arrastre los controladores de tamaño para cambiar el tamaño de una imagen o de una parte de ella. Los controladores de tamaño que puede arrastrar son sólidos. No se pueden arrastrar los manipuladores que están huecos. Use la ventana **propiedades** para cambiar el tamaño solo de la imagen completa, no de un elemento seleccionado.

![Controladores de tamaño de un mapa de bits](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Controladores de tamaño

> [!NOTE]
> Si tiene la opción **cuadrícula de mosaico** seleccionada en el [cuadro de diálogo Configuración](../windows/grid-settings-dialog-box-image-editor-for-icons.md)de la cuadrícula, el cambio de tamaño se ajusta a la siguiente línea de cuadrícula de mosaico. Si solo se selecciona la opción de **cuadrícula de píxeles** (la configuración predeterminada), el cambio de tamaño se ajusta al siguiente píxel disponible.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Para cambiar el tamaño de una imagen completa mediante la ventana Propiedades

1. Abra la imagen cuyas propiedades desea cambiar.

1. En los cuadros **ancho** y **alto** del [ventana Propiedades](/visualstudio/ide/reference/properties-window), escriba las dimensiones que desee.

   Si va a aumentar el tamaño de la imagen, el **Editor de imágenes** amplía la imagen hacia la derecha, hacia abajo o ambos, y rellena la nueva región con el color de fondo actual. La imagen no se ajusta.

   Si reduce el tamaño de la imagen, el **Editor de imágenes** recorta la imagen en el borde derecho o inferior, o ambas cosas.

   > [!NOTE]
   > Puede usar las propiedades **ancho** y **alto** para cambiar el tamaño solo de la imagen completa, no para cambiar el tamaño de una selección parcial.

#### <a name="to-crop-or-extend-an-entire-image"></a>Para recortar o ampliar una imagen completa

1. Seleccione toda la imagen.

   Si parte de la imagen está seleccionada actualmente y desea seleccionar toda la imagen, seleccione cualquier parte de la imagen fuera del borde de selección actual.

1. Arrastre un controlador de tamaño hasta que la imagen tenga el tamaño correcto.

Normalmente, el **Editor de imágenes** recorta o amplía una imagen al cambiar su tamaño moviendo un controlador de tamaño. Si mantiene presionada la tecla **MAYÚS** mientras mueve un controlador de tamaño, el **Editor de imágenes** reduce o estira la imagen.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Para reducir o expandir una imagen completa

1. Seleccione toda la imagen.

   Si una parte de la imagen está seleccionada actualmente y desea seleccionar toda la imagen, seleccione cualquier parte de la imagen fuera del borde de selección actual.

1. Mantenga presionada la tecla **MAYÚS** y arrastre un controlador de tamaño hasta que la imagen tenga el tamaño correcto.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Para reducir o ajustar parte de una imagen

1. Seleccione la parte de la imagen cuyo tamaño desea cambiar. Para obtener más información, vea [seleccionar un área de la imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Arrastre uno de los controladores de tamaño hasta que la selección sea el tamaño correcto.

### <a name="to-edit-an-image-outside-of-a-project"></a>Para editar una imagen fuera de un proyecto

Puede abrir y editar imágenes en el entorno de desarrollo tal como lo haría en cualquier aplicación de gráficos, por ejemplo, abriendo un mapa de bits para la edición independiente. Las imágenes con las que trabaja no deben formar parte de un proyecto de Visual Studio.

1. Vaya a **archivo** de menú > **abrir**.

1. En el cuadro **archivos de tipo** , seleccione **todos los archivos**.

1. Busque y abra la imagen que desea editar.

### <a name="to-change-image-properties"></a>Para cambiar las propiedades de la imagen

Puede establecer o modificar las propiedades de una imagen mediante el [ventana Propiedades](/visualstudio/ide/reference/properties-window).

1. Abra la imagen en el **Editor de imágenes**.

1. En la ventana **propiedades** , cambie las propiedades o todas las propiedades de la imagen.

   |Propiedad|Descripción|
   |--------------|-----------------|
   |**Colores**|Especifica la combinación de colores de la imagen. Seleccione **monocromo**, **16**o **256**o **true color**.<br/><br/>Si ya ha dibujado la imagen con una paleta de 16 colores, al seleccionar **monocromo** , se producen sustituciones de color negro y blanco para los colores de la imagen. No siempre se mantiene el contraste: por ejemplo, las áreas adyacentes de rojo y verde se convierten en negro.|
   |**Nombre de archivo**|Especifica el nombre del archivo de imagen.<br/><br/>De forma predeterminada, Visual Studio asigna un nombre de archivo base creado quitando los cuatro primeros caracteres ("IDB_") del identificador de recursos predeterminado (IDB_BITMAP1) y agregando la extensión adecuada. El nombre de archivo de la imagen de este ejemplo sería *BITMAP1. bmp*. Podría cambiarle el nombre por *MYBITMAP1. bmp*.|
   |**Height**|Establece el alto de la imagen (en píxeles). El valor predeterminado es 48.<br/><br/>La imagen se recorta o se agrega espacio en blanco debajo de la imagen existente.|
   |**Id**|Establece el identificador del recurso.<br/><br/>En el caso de una imagen, Microsoft Visual Studio, de forma predeterminada, asigna el siguiente identificador disponible en una serie: IDB_BITMAP1, IDB_BITMAP2, etc. Se usan nombres similares para iconos y cursores.|
   |**Índ**|Cambia las propiedades de color.<br/><br/>Haga doble clic para seleccionar un color y mostrar el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Defina el color escribiendo los valores RGB o HSL en los cuadros de texto correspondientes.|
   |**SaveCompressed**|Indica si la imagen está en un formato comprimido. Esta propiedad es de solo lectura.<br/><br/>Visual Studio no permite guardar imágenes en formato comprimido, de modo que para las imágenes creadas en Visual Studio, esta propiedad será **false**. Si abre una imagen comprimida (creada en otro programa) en Visual Studio, esta propiedad será **true**. Si guarda una imagen comprimida con Visual Studio, se descomprime y esta propiedad se revertirá a **false**.|
   |**Width**|Establece el ancho de la imagen (en píxeles). El valor predeterminado para los mapas de bits es 48.<br/><br/>La imagen se recorta o se agrega espacio en blanco a la derecha de la imagen existente.|

## <a name="requirements"></a>Requisitos

None

## <a name="see-also"></a>Consulte también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: crear un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Cómo: usar una herramienta de dibujo](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Cómo: trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
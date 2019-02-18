---
title: Filtrar Trabajar con colores
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: e91767083f54df0b1b30833337cfed603dc331ff
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336649"
---
# <a name="how-to-work-with-color"></a>Procedimiento Trabajar con colores

El **Editor de imágenes** contiene muchas características que controlan específicamente y personalización los colores. Puede establecer el color de primer plano o en segundo plano, rellenar áreas delimitadas con color o seleccione un color en una imagen que se usará como el color de primer plano o actual. Puede usar herramientas en el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) junto con la paleta de colores en el **colores** ventana para crear imágenes.

Se muestran todos los colores para monocromo e imágenes de 16 colores en el **colores** paleta en la **colores** ventana. Junto con los 16 colores estándares, puede crear sus propios colores personalizados. Si se cambia cualquiera de los colores de la paleta cambiará inmediatamente el color correspondiente en la imagen.

Cuando se trabaja con el icono de 256 colores e imágenes de cursor, la **colores** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window) se utiliza. Para obtener más información, consulte [crear un icono de 256 colores o cursor](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

> [!NOTE]
> Mediante el **Editor de imágenes**, puede ver las imágenes de 32 bits, pero no puede modificarlas.

También se pueden crear imágenes de color verdadero. Sin embargo, las muestras de color verdadero no aparecen en la paleta completa de la **colores** ventana; aparecen sólo en el área de indicador de color de primer plano o en segundo plano. Verdadero se crea mediante el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md).

Puede guardar las paletas de colores personalizada en el disco y volver a cargarlos según sea necesario. La paleta de colores usados más recientemente se guarda en el registro y se cargan automáticamente la próxima vez que inicie Visual Studio.

El **colores** ventana consta de dos partes:

- El **paleta de colores**, que es una matriz de muestras de color que representan los colores que puede utilizar. Puede seleccionar los ejemplos para elegir los colores de primer y segundo plano cuando está usando las herramientas de gráficos.

- El **indicador de Color**, que muestra los colores de primer y segundo plano y selectores de colores de pantalla e inversos.

   ![Ventana colores](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   Ventana Colores

> [!NOTE]
> El **pantalla color** y **color inverso** herramientas solo están disponibles para iconos y cursores.

Puede usar el **colores** ventana con el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md).

- Para mostrar el **colores** ventana, el botón secundario en un **Editor de imágenes** panel y elija **Mostrar ventana colores**, o bien seleccione **Mostrar ventana colores**en el [menú imagen](../windows/image-menu-image-editor-for-icons.md).

- Para ocultar el **colores** ventana, Desanclar de la ventana (esta acción permitirá que la ventana de ocultación automática cuando no está en uso) o seleccione el **cerrar** botón.

El **colores** paleta muestra inicialmente los 16 colores estándar. Con los colores mostrados, también puede crear sus propios colores personalizados. A continuación, puede guardar y cargar una paleta de colores personalizada.

El **Selector de colores personalizados** cuadro de diálogo le permite personalizar los colores utilizados para la imagen. Las siguientes propiedades que se incluyen son:

|Property|Descripción|
|--------------------------|--------------------------|
|**Presentación de Color degradado**|Cambia los valores de un color seleccionado. Coloque la cruz en el color que desee cambiar. A continuación, mueva el control deslizante hacia arriba o hacia abajo para cambiar la luminosidad o los valores RGB del color.|
|**Barra Luminosidad**|Establece la luminosidad del color seleccionado en el **muestra de Color degradado** cuadro. Seleccione y arrastre la flecha blanca de la barra para aumentar el brillo o hacia abajo para menor. El **Color** cuadro muestra el color que ha seleccionado y el efecto de la luminosidad establece.|
|**Color**|Muestra el matiz (valor de la rueda de colores) del color que se va a definir. El intervalo de valores está comprendido entre 0 y 240, donde 0 es rojo, 60 es amarillo, 120 es verde, 180 es aguamarina, 200 es magenta y 240 es azul.|
|**HUE**|Muestra el matiz (valor de la rueda de colores) del color que se va a definir. El intervalo de valores está comprendido entre 0 y 240, donde 0 es rojo, 60 es amarillo, 120 es verde, 180 es aguamarina, 200 es magenta y 240 es azul.|
|**Sáb**|Especifica el valor de saturación del color que se va a definir. La saturación es la cantidad de color en un matiz especificado. Los valores comprendidos entre 0 y 240.|
|**Lum.**|Enumera la luminosidad (brillo) del color que se va a definir. Los valores comprendidos entre 0 y 240.|
|**Red**|Especifica el valor de color rojo del color que se va a definir. El intervalo de valores está comprendido entre 0 y 255.|
|**Green**|Especifica el valor de color verde del color que se va a definir. El intervalo de valores está comprendido entre 0 y 255.|
|**Blue**|Especifica el valor azul del color que se va a definir. El intervalo de valores está comprendido entre 0 y 255.|

Puede guardar y cargar un **colores** paleta que contiene colores personalizados. (De forma predeterminada, el **colores** paleta usado más recientemente se carga automáticamente al iniciar Visual Studio.)

> [!TIP]
> Puesto que la **imagen** editor no tiene ningún medio para restaurar el valor predeterminado **colores** paleta, debe guardar el valor predeterminado **colores** paleta en un nombre, como  *estándar.PAL* o *predeterminada.PAL* por lo que puede restaurar fácilmente la configuración predeterminada.

Utilice la **Cargar paleta de colores** cuadro de diálogo para cargar las paletas de colores para usar en el proyecto de C++. Las siguientes propiedades que se incluyen son:

|Property|Descripción|
|-----------------|-----------------|
|**Buscar en**|Especifica la ubicación donde desea ubicar un archivo o carpeta. Seleccione la flecha para elegir otra ubicación, o seleccione el icono de carpeta en la barra de herramientas para mover los niveles.|
|**Nombre de archivo**|Proporciona un espacio para que escriba el nombre del archivo que desea abrir. Para buscar rápidamente un archivo que ha abierto anteriormente, seleccione el nombre de archivo en la lista desplegable, si está disponible.<br/><br/>Si está buscando un archivo, puede utilizar asteriscos (*) como caracteres comodín. Por ejemplo, puede escribir \*.\* para ver una lista de todos los archivos. También puede escribir la ruta de acceso completa de un archivo, por ejemplo, C:\My Documentos\MiPaletaDeColores. PAL o \\\NetworkServer\MyFolder\MyColorPalette.pal.|
|**Tipo de archivo**|Enumera los tipos de archivos que se va a mostrar. Paleta (*. PAL) es el tipo de archivo predeterminado para las paletas de colores.|

## <a name="how-to"></a>Procedimientos

### <a name="to-select-foreground-or-background-colors"></a>Para seleccionar los colores de primer plano o en segundo plano

Excepto para el **borrador**, las herramientas en el **Editor de imágenes** draw de la barra de herramientas con el color actual de primer plano o en segundo plano cuando se presiona el botón izquierdo o derecho del mouse, respectivamente.

- Para seleccionar un color de primer plano, con el botón primario del mouse, seleccione el color que desee en el **colores** paleta.

- Para seleccionar un color de fondo, con el botón secundario del mouse, seleccione el color que desee en el **colores** paleta.

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>Para rellenar un área delimitada de una imagen con un color

El editor de imágenes ofrece el **rellenar** herramienta para rellenar alguna entre el área de la imagen con el color de dibujo actual o el color de fondo actual.

> [!TIP]
> Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

### <a name="to-use-the-fill-tool"></a>Para usar la herramienta relleno

1. En el **Editor de imágenes** barra de herramientas (o use **imagen** > **herramientas**), seleccione el **rellenar** herramienta.

1. Si es necesario, elija los colores de dibujo: En el [paleta de colores](../windows/colors-window-image-editor-for-icons.md), seleccione el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.

1. Mover el **relleno** herramienta para el área que desea rellenar.

1. Seleccione el botón izquierdo o derecho del mouse para rellenar con el color de primer plano o el color de fondo, respectivamente.

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>Para elegir un color de una imagen para usar en otro lugar

El **seleccionar Color**, o convierta, herramienta hace que cualquier color en la imagen el color de primer plano actual o el color de fondo, dependiendo de si presiona el botón secundario del mouse o la izquierda. Para cancelar la **seleccionar Color** de herramientas, elija otra herramienta.

> [!TIP]
> Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

#### <a name="to-pick-up-a-color"></a>Para seleccionar un color

1. En el **Editor de imágenes** barra de herramientas (o desde el **imagen** menú, **herramientas** comando), seleccione el **seleccionar Color** herramienta.

1. Seleccione el color que desee para recoger de la imagen.

   > [!NOTE]
   > Después de seleccionar un color, el **imagen** herramienta del editor se reactiva usado más recientemente.

1. Dibujar con el botón primario del mouse para el color de primer plano o en el botón secundario del mouse para el color de fondo.

### <a name="to-choose-the-background"></a>Para elegir el fondo

Al mover o copiar una selección de una imagen, los píxeles de la selección que coinciden con el color de fondo actual son transparentes de forma predeterminada, y estos no oscurecen píxeles en la ubicación de destino.

Puede cambiar de un fondo transparente (valor predeterminado) a un fondo opaco y viceversa. Cuando se usa una herramienta de selección, el **fondo transparente** y **fondo opaco** opciones aparecen en la **opción** selector en la **delEditordeimágenes** barra de herramientas (como se muestra a continuación).

![Opciones de fondo &#45; opaca o transparente](../windows/media/vcimageeditoropaqtranspback.gif "en segundo plano opciones &#45; opaca o transparente")<br/>
**Opciones transparentes y opacas** en el **barra de herramientas del Editor de imágenes**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Para cambiar entre un fondo transparente y opaco

En el **Editor de imágenes** barra de herramientas, seleccione el **opción** selector y, a continuación, elija el icono correspondiente:

- `Opaque Background (O)`: Todas las partes de la selección oscurecen la imagen existente.

- `Transparent Background (T)`: Imagen existente se muestra en las partes de la selección que coinciden con el color de fondo actual.

   \- o -

En el **imagen** menú, active o desactive **dibujar figuras opacas**.

Puede cambiar el color de fondo mientras una selección ya está en vigor para cambiar qué partes de la imagen son transparentes.

### <a name="to-invert-the-colors-in-a-selection"></a>Para invertir los colores de una selección

El **imagen** editor proporciona una manera cómoda de invertir los colores de la parte seleccionada de la imagen de forma que puede saber cómo se vería una imagen con los colores invertidos.

Invertir los colores de la selección actual, en el **imagen** menú, seleccione **invertir colores**.

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>Para personalizar o cambiar los colores de la paleta de colores

1. Desde el **imagen** menú, elija **Ajustar colores**.

1. En el **Selector de colores personalizados** diálogo cuadro, defina el color escribiendo los valores RGB o HSL en los cuadros de texto correspondientes o elija un color en el **muestra de Color degradado** cuadro.

1. Establezca la luminosidad moviendo el control deslizante el **luminosidad** barra.

1. Muchos colores personalizados están interpolados. Si desea que el color sólido más próximo al color interpolado, haga doble clic en el **Color** cuadro.

   Si más adelante decide que desea el color interpolado, mueva el control deslizante el **luminosidad** barra o mueva la cruz el **muestra de Color degradado** cuadro de nuevo para restaurar la interpolación.

1. Seleccione **Aceptar** para agregar el nuevo color.

### <a name="to-save-a-custom-colors-palette"></a>Para guardar una paleta de colores personalizada

1. Desde el **imagen** menú, elija **Guardar paleta**.

1. Desplácese al directorio donde quiera guardar la paleta y escriba un nombre para la misma.

1. Seleccione **Guardar**.

### <a name="to-load-a-custom-colors-palette"></a>Para cargar una paleta de colores personalizada

1. Desde el **imagen** menú, elija **Cargar paleta**.

1. En el **Cargar paleta de colores** diálogo cuadro, vaya al directorio correcto y seleccione la paleta que desea cargar. **Color** paletas se guardan con una extensión de archivo. PAL.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Crear zonas transparentes o inversas en las imágenes de dispositivo](../windows/creating-transparent-or-inverse-regions-in-device-images.md)<br/>
[Cuadro de diálogo Selector de colores personalizada](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Imagen (menú)](../windows/image-menu-image-editor-for-icons.md)<br/>

---
title: Editor de imágenes para iconos
ms.date: 10/17/2018
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
- Image menu
- Grid Settings dialog box [C++]
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: 48b363b7b9021042fe6242be70c74f0daeade0c2
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320710"
---
# <a name="image-editor-for-icons"></a>Editor de imágenes para iconos

Al hacer clic en un archivo de imagen (por ejemplo, .ico, .bmp, .png) en el Explorador de soluciones, la imagen se abre en el Editor de imágenes de la misma manera que los archivos de código abierto en el Editor de código. Cuando está activa una pestaña del Editor de imágenes, vea las barras de herramientas con muchas herramientas para crear y editar imágenes. Junto con los mapas de bits, iconos y cursores, pueden editarse imágenes en formato GIF o JPEG mediante los comandos el **imagen** menú y las herramientas de la **Editor de imágenes** barra de herramientas.

Recursos gráficos son las imágenes que se definen para la aplicación. Puede dibujar a mano alzada o dibujar mediante formas. Puede seleccionar partes de una imagen para editar, voltear o cambiar el tamaño, o puede crear un pincel personalizado de una parte seleccionada de una imagen y dibujar con pincel. Puede definir propiedades de la imagen, guardar imágenes en diferentes formatos y convertir las imágenes de un formato a otro.

Además de crear nuevos recursos gráficos, puede [importar imágenes existentes](../windows/how-to-import-and-export-resources.md) para editarlo y, a continuación, agréguelos al proyecto. También puede abrir y editar las imágenes que no forman parte de un proyecto para [edición de imágenes independientes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

> [!NOTE]
> Mediante el **Editor de imágenes**, puede ver las imágenes de 32 bits, pero no puede modificarlas.

Con el Editor de imágenes, se puede:

- [Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)

- [Trabajar con iconos y cursores: Recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [Usar teclas de aceleración para comandos del Editor de imágenes](../windows/accelerator-keys-image-editor-for-icons.md)

El **Editor de imágenes** ventana muestra dos vistas de una imagen, con una barra que separa los dos paneles de división. Se puede arrastrar dicha barra a uno u otro lado para cambiar el tamaño relativo de los paneles. El panel activo muestra un borde de selección.

El **Editor de imágenes** ventana puede ajustarse para ajustarse a sus necesidades y preferencias. Se puede [cambiar el factor de ampliación](../windows/changing-the-magnification-factor-image-editor-for-icons.md) y [mostrar u ocultar la cuadrícula de píxeles](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).

> [!NOTE]
> Mediante el **Editor de imágenes**, puede ver las imágenes de 32 bits, pero no puede modificarlas.

## <a name="image-menu"></a>Imagen (Menú)

El **imagen** menú, que solo aparece cuando el **imagen** editor está activo, tiene comandos para editar imágenes, administrar las paletas de colores y establecer **Editor de imágenes** ventana Opciones. Además, los comandos para el uso de las imágenes de dispositivo están disponibles al trabajar con iconos y cursores.

|Comando|Descripción|
|---|---|
|**Invertir colores**|Invierte los colores. Para obtener más información, consulte [invertir los colores de una selección](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).|
|**Voltear horizontalmente**|Voltea la imagen o la selección en sentido horizontal. Para obtener más información, consulte [voltear una imagen](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Voltear verticalmente**|Voltea la imagen o la selección en sentido vertical. Para obtener más información, consulte [voltear una imagen](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Girar 90 grados**|Gira la imagen o la selección 90 grados. Para obtener más información, consulte [voltear una imagen](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Mostrar ventana colores**|Se abre el [ventana colores](../windows/colors-window-image-editor-for-icons.md), en la que puede elegir los colores que se usará para la imagen. Para obtener más información, consulte [trabajar con colores](../windows/working-with-color-image-editor-for-icons.md).|
|**Usar la selección como pincel**|Le permite crear un pincel personalizado desde una parte de una imagen. La selección se convierte en un pincel personalizado que distribuye los colores de la selección en la imagen. Copias de la selección se dejan a lo largo de la trayectoria de arrastre. Cuanto más lentamente arrastre, se realizan las copias más. Para obtener más información, consulte [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).|
|**Copiar y resaltar selección**|Crea una copia de la selección actual y la resalta. Si la selección actual contiene el color de fondo, se excluirá si ha [transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) seleccionado.
|**Ajustar colores**|Se abre el [Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), que le permite personalizar los colores utilizados para la imagen. Para obtener más información, consulte [personalizar o cambiar colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md).|
|**Cargar paleta**|Se abre el [cuadro de diálogo Cargar paleta de colores](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), lo que permite cargar paleta de colores previamente guarda en un archivo. PAL.|
|**Guardar paleta**|Guarda la paleta de colores en un archivo. PAL.|
|**Dibujar figuras opacas**|Cuando se selecciona, convierte la selección actual en opaca. Cuando está desactivada, clarifica la selección actual. Para obtener más información, consulte [elegir un fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|**Editor de barras de herramientas**|Se abre el [cuadro de diálogo nuevo recurso de barra de herramientas](../windows/new-toolbar-resource-dialog-box.md).|
|**Configuración de la cuadrícula**|Se abre el **configuración de la cuadrícula** cuadro de diálogo en el que puede especificar las cuadrículas para la imagen.|
|**Nuevo tipo de imagen**|Se abre el [New \<dispositivo > cuadro de diálogo de tipo de imagen](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Un solo recurso de icono puede contener varias imágenes de diferentes tamaños y windows pueden usar el tamaño de icono apropiado dependiendo de cómo se va a mostrarse. Un nuevo tipo de dispositivo no modifica el tamaño del icono, sino que crea una nueva imagen del icono. Solo se aplica a los iconos y cursores.|
|**Tipo de imagen de icono o Cursor actual**|Se abre un submenú que muestra el primer icono o cursor imágenes disponibles (los primeros nueve). El último comando en el submenú, **más...** , se abre el [abierto \<dispositivo > cuadro de diálogo imagen](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Eliminar tipo de imagen**|Elimina la imagen del dispositivo seleccionado.|
|**Herramientas**|Inicia un submenú que contiene todas las herramientas disponibles desde el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md).|

El **configuración de la cuadrícula** cuadro de diálogo le permite especificar la configuración de la cuadrícula para la imagen y muestra las líneas de cuadrícula a lo largo de la imagen editada. Las líneas son útiles para editar la imagen, pero no se guardan como parte de la imagen en Sí.

|Property|Descripción|
|---|---|
|**Cuadrícula de píxeles**|Cuando está activada, se muestra una cuadrícula alrededor de cada píxel en el editor de imágenes. La cuadrícula aparece sólo en 4 × y resoluciones más altas.|
|**Cuadrícula de mosaico**|Cuando se selecciona, muestra una cuadrícula alrededor de los bloques de píxeles en el editor de imágenes, especificado por los valores de espaciado de cuadrícula.|
|**Width**|Especifica el ancho de cada bloque del mosaico. Esta propiedad es útil al dibujar mapas de bits que contiene varias imágenes que se organizan en intervalos regulares.|
|**Height**|Especifica el alto de cada bloque del mosaico. Esta propiedad es útil al dibujar mapas de bits que contiene varias imágenes que se organizan en intervalos regulares.|

## <a name="toolbar"></a>Barra de herramientas

El **Editor de imágenes** barra de herramientas contiene herramientas de dibujo, pintura, escribir texto, borrado y manipulación de vistas. También contiene un selector de opciones, con el que puede seleccionar opciones para usar cada herramienta. Por ejemplo, puede elegir desde diversos anchos de pincel, factores de ampliación y estilos de línea.

> [!NOTE]
> Todas las herramientas disponibles en el **Editor de imágenes** también están disponibles en la barra de herramientas del **imagen** menú (bajo la **herramientas** comando).

![Barra de herramientas del Editor de imágenes](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") barra de herramientas del Editor de imágenes

Para usar el **Editor de imágenes** barra de herramientas y **opción** selector, seleccione la herramienta o la opción que desee.

> [!TIP]
> Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

Con el **opción** selector se puede especificar el ancho de una línea, el trazo de pincel y mucho más. En el icono del **opción** cambios de botón de selector según la herramienta que ha seleccionado.

![Dibujo&#45;selector con forma de la barra de herramientas del Editor de imágenes](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") Selector de opciones en la barra de herramientas del Editor de imágenes

### <a name="use-the-text-tool-dialog-box"></a>Utilice el cuadro de diálogo Herramienta de texto

Use la **texto herramienta** cuadro de diálogo para agregar texto a un recurso de cursor, mapa de bits o icono.

Para obtener acceso a este cuadro de diálogo, abra el [Editor de imágenes](../windows/window-panes-image-editor-for-icons.md). Seleccione **herramientas** desde el **imagen** menú y, a continuación, seleccione el **texto herramienta** comando.

#### <a name="font-button"></a>Botón de fuente

Se abre el **fuente de herramienta de texto** cuadro de diálogo, en el que puede cambiar la fuente, estilo o tamaño de la fuente del cursor. Los cambios se aplican al texto que se muestra en el **texto** área.

Para obtener acceso a este cuadro de diálogo, seleccione el **fuente** situado en la **texto herramienta** cuadro de diálogo. Las propiedades disponibles son:

|Property|Descripción|
|---|---|
|**Fuente**|Enumera las fuentes disponibles.|
|**Estilo de fuente**|Se enumeran los estilos disponibles para la fuente especificada.|
|**Size**|Enumera los tamaños de punto disponibles para la fuente especificada.|
|**Ejemplo**|Muestra un ejemplo de cómo aparecerá el texto con la configuración de fuente especificado.|
|**Script**|Enumera las secuencias de comandos de idioma disponibles para la fuente especificada. Cuando se selecciona un script de idioma diferente, el juego de caracteres para ese idioma estará disponible para la creación de documentos en varios idiomas.|

Para cambiar la fuente del texto de una imagen:

El procedimiento siguiente es un ejemplo de cómo agregar texto a un icono en una aplicación de Windows y manipular la fuente del texto.

1. Cree una aplicación de formularios de Windows de C++. Para obtener más información, consulte [crear un proyecto de aplicación Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5). Un *app.ico* archivo se agrega al proyecto de forma predeterminada.

1. En **el Explorador de soluciones**, haga doble clic en el archivo *app.ico*. El [Editor de imágenes](../windows/image-editor-for-icons.md) se abrirá.

1. Desde el **imagen** menú, seleccione **herramientas** y, a continuación, seleccione **texto herramienta**. El **texto herramienta** aparecerá el cuadro de diálogo.

1. En el **texto herramienta** cuadro de diálogo, escriba *C++* en el área de texto vacío. Este texto aparecerá en un cuadro de tamaño ajustable ubicado en la esquina superior izquierda de *app.ico*, en el **Editor de imágenes**.

1. En el **Editor de imágenes**, arrastre el cuadro de tamaño variable en el centro del archivo app.ico para mejorar la legibilidad del texto.

1. En el **texto herramienta** cuadro de diálogo, seleccione el **fuente** botón. El **fuente de herramienta de texto** aparecerá el cuadro de diálogo.

1. En el **fuente de herramienta de texto** cuadro de diálogo, seleccione **Times New Roman** en la lista de fuentes disponibles que aparecen en la **fuente** cuadro de lista.

1. Seleccione **negrita** en la lista de estilos de fuentes disponibles aparecen en la **estilo de fuente** cuadro de lista.

1. Seleccione **10** en la lista de disponibles, seleccione tamaños que se muestran en el **tamaño** cuadro de lista.

1. Seleccione el botón **Aceptar**. El **fuente de herramienta de texto** cuadro de diálogo se cerrará y se aplicará la nueva configuración de fuente al texto.

1. Seleccione el **cerrar** situado en la **texto herramienta** cuadro de diálogo. El cuadro de tamaño ajustable alrededor del texto desaparecerá de la **Editor de imágenes**.

#### <a name="text-area"></a>Área de texto

Muestra el texto que aparece como parte del recurso. Inicialmente, esta área está vacía.

> [!NOTE]
> Si **fondo transparente** está establecido, sólo el texto se colocará en la imagen. Si **fondo opaco** está establecido, un rectángulo delimitador, relleno con el [color de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), se colocarán detrás del texto. Para obtener más información, consulte [elegir opaco y fondos transparentes](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Puede haga doble clic en el **texto herramienta** cuadro de diálogo para tener acceso a un menú contextual predeterminado que contiene una lista de comandos de Windows estándar.

### <a name="to-display-or-hide-the-image-editor-toolbar"></a>Para mostrar u ocultar la barra de herramientas del Editor de imágenes

Puesto que muchas de las herramientas de dibujo están disponibles desde el [teclado](../windows/accelerator-keys-image-editor-for-icons.md), a veces resulta útil ocultar el **Editor de imágenes** barra de herramientas.

En el **vista** menú, seleccione **las barras de herramientas** , a continuación, elija **Editor de imágenes**.

   > [!NOTE]
   > Los elementos de esta barra de herramientas aparecerán no están disponibles cuando un archivo de imagen del proyecto actual o la solución no está abierta en el **Editor de imágenes**. Consulte [creación de un icono o imagen otras](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), para obtener información sobre cómo agregar archivos de imagen a sus proyectos.

## <a name="window-panes"></a>Paneles de la ventana

El **Editor de imágenes** ventana muestra una imagen de normalmente en dos paneles separados por una barra divisora. Una vista es el tamaño real y la otra se amplía (el factor de ampliación predeterminado es 6). Las vistas de estos dos paneles se actualizan automáticamente: los cambios realizados en un panel se muestran inmediatamente en el otro. Los dos paneles facilitan el trabajo en la vista ampliada de la imagen, en el que pueda distinguir los píxeles individuales y, al mismo tiempo, observar el efecto del trabajo en la vista de tamaño real de la imagen.

Utiliza el espacio se necesita el panel izquierdo (la mitad de la **imagen** ventana) para mostrar la vista de ampliación 1:1 (valor predeterminado) de la imagen. El panel derecho muestra la imagen ampliada (ampliación 6:1 de forma predeterminada). Puede cambiar la ampliación de cada panel utilizando el **Magnify** herramienta en el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o mediante las teclas de aceleración.

Puede ampliar el panel menor de la **Editor de imágenes** ventana y usar los dos paneles para mostrar diferentes regiones de una imagen grande. Seleccione esta opción dentro del panel para elegirlo.

Puede cambiar el tamaño relativo de los paneles colocando el puntero en la barra de división y al mover la barra de división hacia la izquierda o derecha. Si desea trabajar en un solo panel, puede mover la barra de división a ambos lados.

Si el **Editor de imágenes** panel es ampliada por un factor de 4 o mayor, puede mostrar una cuadrícula de píxeles que delimita los píxeles individuales de la imagen.

### <a name="to-change-the-magnification-factor"></a>Para cambiar el factor de ampliación

De forma predeterminada, el **imagen** editor muestra la vista en el panel izquierdo al tamaño real y la vista en el panel derecho a las 6 veces el tamaño real. El factor de ampliación (que se muestra en la barra de estado en la parte inferior del área de trabajo) es la relación entre el tamaño real de la imagen y el tamaño de muestra. El factor de forma predeterminada es 6 y el intervalo es de 1 a 10.

1. Seleccione el **Editor de imágenes** panel cuyo factor de ampliación que desee cambiar.

1. En el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md), seleccione la flecha situada a la derecha de la [herramienta aumentar](../windows/toolbar-image-editor-for-icons.md) y seleccione el factor de ampliación desde el submenú: **1 X**, **2 X**, **6 X**, o **8 X**.

   > [!NOTE]
   > Para seleccionar un factor de ampliación que no aparecen en la **Magnify** herramienta, utilice las teclas de aceleración.

### <a name="to-display-or-hide-the-pixel-grid"></a>Para mostrar u ocultar la cuadrícula de píxeles

Para todos los **Editor de imágenes** paneles con un factor de ampliación de 4 o superior, puede mostrar una cuadrícula que delimita los píxeles individuales de la imagen.

1. En el **imagen** menú, seleccione **configuración de la cuadrícula**.

1. Seleccione el **cuadrícula de píxeles** casilla de verificación para mostrar la cuadrícula, o desactive la casilla para ocultar la cuadrícula.

> [!TIP]
> Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

## <a name="visual-studio-image-library"></a>Biblioteca de imágenes de Visual Studio

Puede descargar de forma gratuita la **biblioteca de imágenes de Visual Studio** que contiene muchas animaciones, mapas de bits e iconos que puede usar en sus aplicaciones. Para obtener más información sobre cómo descargar la biblioteca, vea [La biblioteca de imágenes de Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="managed-resources"></a>Recursos administrados

Puede usar el **imagen** editor y la [editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Iconos](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)
---
title: Editor de imágenes para iconos (C++)
ms.date: 02/15/2019
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
ms.openlocfilehash: dd7da76d3df68fa63c87f64610524accfd4302ef
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041554"
---
# <a name="image-editor-for-icons-c"></a>Editor de imágenes para iconos (C++)

Cuando selecciona un archivo de imagen (por ejemplo, .ico, .bmp, .png) en **el Explorador de soluciones**, la imagen se abre en el **Editor de imágenes** de la misma manera que se abren los archivos de código en el **Editor de código** . Cuando un **Editor de imágenes** pestaña está activa, consulte las barras de herramientas con muchas herramientas para crear y editar imágenes. Junto con los mapas de bits, iconos y cursores, pueden editarse imágenes en formato GIF o JPEG mediante los comandos el **imagen** menú y las herramientas de la **Editor de imágenes** barra de herramientas.

Recursos gráficos son las imágenes que se definen para la aplicación. Puede dibujar a mano alzada o dibujar mediante formas. Puede seleccionar partes de una imagen para editar, voltear o cambiar el tamaño, o puede crear un pincel personalizado de una parte seleccionada de una imagen y dibujar con pincel. Puede definir propiedades de la imagen, guardar imágenes en diferentes formatos y convertir las imágenes de un formato a otro.

> [!NOTE]
> Mediante el **Editor de imágenes**, puede ver las imágenes de 32 bits, pero no puede modificarlas.

También puede usar el **Editor de imágenes** y [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

Además de crear nuevos recursos gráficos, puede [importar imágenes existentes](../windows/how-to-copy-resources.md#import-and-export-resources) para editarlo y, a continuación, agréguelos al proyecto. También puede abrir y editar las imágenes que no forman parte de un proyecto para [edición de imágenes independientes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

Para obtener información sobre la **Editor de imágenes**, vea cómo [crear un icono o imagen otras](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [editar una imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [usar una herramienta de dibujo](../windows/using-a-drawing-tool-image-editor-for-icons.md), [Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md), y [teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Descargar de forma gratuita la **biblioteca de imágenes de Visual Studio** que contiene muchas animaciones, mapas de bits e iconos que puede usar en sus aplicaciones. Para obtener más información sobre cómo descargar la biblioteca, consulte el [biblioteca de imágenes de Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Imagen (Menú)

El **imagen** menú, que solo aparece cuando el **Editor de imágenes** está activa, tiene comandos para editar imágenes, administrar las paletas de colores y establecer **Editor de imágenes** ventana Opciones. Además, los comandos para el uso de las imágenes de dispositivo están disponibles al trabajar con iconos y cursores.

|Comando|Descripción|
|---|---|
|**Invertir colores**|Invierte los colores.|
|**Voltear horizontalmente**|Voltea la imagen o la selección en sentido horizontal.|
|**Voltear verticalmente**|Voltea la imagen o la selección en sentido vertical.|
|**Girar 90 grados**|Gira la imagen o la selección 90 grados.|
|**Mostrar ventana colores**|Se abre el **colores** ventana, en el que puede elegir los colores que se usará para la imagen.|
|**Usar la selección como pincel**|Le permite crear un pincel personalizado desde una parte de una imagen.<br/><br/>La selección se convierte en un pincel personalizado que distribuye los colores de la selección en la imagen. Copias de la selección se dejan a lo largo de la trayectoria de arrastre. Cuanto más lentamente arrastre, se realizan las copias más.|
|**Copiar y resaltar selección**|Crea una copia de la selección actual y la resalta.<br/><br/>Si la selección actual contiene el color de fondo, se excluirá si ha transparente seleccionado.
|**Ajustar colores**|Se abre el **Selector de colores personalizados**, que le permite personalizar los colores utilizados para la imagen.|
|**Cargar paleta**|Se abre el **Cargar paleta de colores** cuadro de diálogo que le permite cargar paleta de colores previamente guarda en un archivo. PAL.|
|**Guardar paleta**|Guarda la paleta de colores en un archivo. PAL.|
|**Dibujar figuras opacas**|Cuando se selecciona, convierte la selección actual en opaca.<br/><br/>Cuando está desactivada, clarifica la selección actual.|
|**Editor de barras de herramientas**|Se abre el [cuadro de diálogo nuevo recurso de barra de herramientas](../windows/new-toolbar-resource-dialog-box.md).|
|**Configuración de la cuadrícula**|Se abre el **configuración de la cuadrícula** cuadro de diálogo en el que puede especificar las cuadrículas para la imagen.|
|**Nuevo tipo de imagen**|Se abre el [New \<dispositivo > cuadro de diálogo de tipo de imagen](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Un solo recurso de icono puede contener varias imágenes de diferentes tamaños y windows pueden usar el tamaño de icono apropiado dependiendo de cómo se va a mostrarse. Un nuevo tipo de dispositivo no modifica el tamaño del icono, sino que crea una nueva imagen del icono. Solo se aplica a los iconos y cursores.|
|**Tipo de imagen de icono o Cursor actual**|Se abre un submenú que se muestra las primeros nueve imágenes disponibles icono o cursor. El último comando en el submenú, **más**, se abre el [abierto \<dispositivo > cuadro de diálogo imagen](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Eliminar tipo de imagen**|Elimina la imagen del dispositivo seleccionado.|
|**Herramientas**|Inicia un submenú que contiene todas las herramientas disponibles desde el **Editor de imágenes** barra de herramientas.|

El **configuración de la cuadrícula** cuadro de diálogo le permite especificar la configuración de la cuadrícula para la imagen y muestra las líneas de cuadrícula a lo largo de la imagen editada. Las líneas son útiles para editar la imagen, pero no se guardan como parte de la imagen en Sí.

|Propiedad|Descripción|
|---|---|
|**Cuadrícula de píxeles**|Cuando está activada, se muestra una cuadrícula alrededor de cada píxel de la **Editor de imágenes**.<br/><br/>La cuadrícula aparece sólo en 4 × y resoluciones más altas.|
|**Cuadrícula de mosaico**|Cuando se selecciona, muestra una cuadrícula alrededor de los bloques de píxeles de la **Editor de imágenes**, especificado por los valores de espaciado de cuadrícula.|
|**Width**|Especifica el ancho de cada bloque del mosaico.<br/><br/>Esta propiedad es útil al dibujar mapas de bits que contiene varias imágenes que se organizan en intervalos regulares.|
|**Height**|Especifica el alto de cada bloque del mosaico.<br/><br/>Esta propiedad es útil al dibujar mapas de bits que contiene varias imágenes que se organizan en intervalos regulares.|

## <a name="toolbar"></a>Barra de herramientas

El **Editor de imágenes** barra de herramientas contiene herramientas de dibujo, pintura, escribir texto, borrado y manipulación de vistas. También contiene un selector de opciones, con el que puede seleccionar opciones para usar cada herramienta. Por ejemplo, puede elegir desde diversos anchos de pincel, factores de ampliación y estilos de línea.

Todas las herramientas disponibles en el **Editor de imágenes** también están disponibles en el menú de barra de herramientas **imagen** > **herramientas**. Para usar el **Editor de imágenes** barra de herramientas y **opción** selector, seleccione la herramienta o la opción que desee.

![Barra de herramientas del Editor de imágenes](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
**Editor de imágenes** barra de herramientas

> [!TIP]
> Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

Puesto que muchas de las herramientas de dibujo están disponibles desde el [teclado](../windows/accelerator-keys-image-editor-for-icons.md), a veces resulta útil ocultar el **Editor de imágenes** barra de herramientas.

- Para mostrar u ocultar el **Editor de imágenes** barra de herramientas, vaya al menú **vista** > **las barras de herramientas** y elija **Editor de imágenes**.

> [!NOTE]
> Los elementos de esta barra de herramientas aparecerán no están disponibles cuando un archivo de imagen del proyecto actual o la solución no está abierta en el **Editor de imágenes**.

### <a name="option-selector"></a>selector de opciones

Con el **opción** selector se puede especificar el ancho de una línea, el trazo de pincel y mucho más. En el icono del **opción** cambios de botón de selector según la herramienta que ha seleccionado.

![Dibujo&#45;selector con forma de la barra de herramientas del Editor de imágenes](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
**Opción** selector en la **Editor de imágenes** barra de herramientas

### <a name="text-tool"></a>Herramienta de texto

Use la **texto herramienta** cuadro de diálogo para agregar texto a un recurso de cursor, mapa de bits o icono.

Para obtener acceso a este cuadro de diálogo, abra el **Editor de imágenes** y vaya al menú **imagen** > **herramientas**, a continuación, seleccione el **texto herramienta** comando.

> [!TIP]
> Puede haga doble clic en el **texto herramienta** cuadro de diálogo para tener acceso a un menú contextual predeterminado que contiene una lista de comandos de Windows estándar.

Abra el **fuente de herramienta de texto** cuadro de diálogo para cambiar la fuente, estilo o tamaño de la fuente del cursor. Los cambios se aplican al texto que se muestra en el **texto** área.

Para obtener acceso a este cuadro de diálogo, seleccione el **fuente** situado en la **texto herramienta** cuadro de diálogo. Las propiedades disponibles son:

|Propiedad|Descripción|
|---|---|
|**Fuente**|Enumera las fuentes disponibles.|
|**Estilo de fuente**|Se enumeran los estilos disponibles para la fuente especificada.|
|**Size**|Enumera los tamaños de punto disponibles para la fuente especificada.|
|**Ejemplo**|Muestra un ejemplo de cómo aparecerá el texto con la configuración de fuente especificado.|
|**Script**|Enumera las secuencias de comandos de idioma disponibles para la fuente especificada.<br/><br/>Cuando se selecciona un script de idioma diferente, el juego de caracteres para ese idioma estará disponible para la creación de documentos en varios idiomas.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Para cambiar la fuente del texto de una imagen

Este es un ejemplo de cómo agregar texto a un icono en una aplicación de Windows y manipular la fuente del texto.

1. Cree una aplicación de formularios de Windows de C++. Para obtener más detalles, vea [Cómo: Crear aplicaciones de Windows Forms](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90)). Un *app.ico* archivo se agrega al proyecto de forma predeterminada.

1. En **el Explorador de soluciones**, haga doble clic en el archivo *app.ico*. El **Editor de imágenes** se abrirá.

1. Vaya al menú **imagen** > **herramientas** y seleccione **texto herramienta**.

1. En el **texto herramienta** cuadro de diálogo, escriba *C++* en el área de texto vacío. Este texto aparecerá en un cuadro de tamaño ajustable ubicado en la esquina superior izquierda de *app.ico* en el **Editor de imágenes**.

1. En el **Editor de imágenes**, arrastre el cuadro de tamaño variable en el centro del *app.ico* para mejorar la legibilidad del texto.

1. En el **texto herramienta** cuadro de diálogo, seleccione el **fuente** botón.

1. En el **fuente de herramienta de texto** cuadro de diálogo:

   - Seleccione **Times New Roman** en la lista de fuentes disponibles que aparecen en la **fuente** cuadro de lista.

   - Seleccione **negrita** en la lista de estilos de fuentes disponibles aparecen en la **estilo de fuente** cuadro de lista.

   - Seleccione **10** en la lista de disponibles, seleccione tamaños que se muestran en el **tamaño** cuadro de lista.

   - Elija **Aceptar**. El **fuente de herramienta de texto** cuadro de diálogo se cerrará y se aplicará la nueva configuración de fuente al texto.

1. Elija **cerrar** en el **texto herramienta** cuadro de diálogo. El cuadro de tamaño ajustable alrededor del texto desaparecerá de la **Editor de imágenes**.

El área de texto muestra el texto que aparece como parte del recurso. Inicialmente, esta área está vacía.

> [!NOTE]
> Si **fondo transparente** está establecido, sólo el texto se colocará en la imagen. Si **fondo opaco** está establecido, un rectángulo rellenado con color de fondo, se colocarán detrás del texto.

## <a name="window-panes"></a>Paneles de la ventana

El **Editor de imágenes** ventana muestra dos vistas de una imagen, con una barra que separa los dos paneles de división. Se puede arrastrar dicha barra a uno u otro lado para cambiar el tamaño relativo de los paneles. El panel activo muestra un borde de selección.

Una vista es el tamaño real y la otra se amplía en un factor de ampliación predeterminado de 6. Las vistas de estos dos paneles se actualizan automáticamente, los cambios que realice en un panel se muestran inmediatamente en el otro. Los dos paneles facilitan el trabajo en la vista ampliada de la imagen, en el que pueda distinguir los píxeles individuales y, al mismo tiempo, observar el efecto del trabajo en la vista de tamaño real de la imagen.

Utiliza el espacio se necesita el panel izquierdo (la mitad de la **imagen** ventana) para mostrar la vista de ampliación 1:1 de forma predeterminada de la imagen. El panel derecho muestra una imagen ampliada de ampliación 6:1 predeterminada. Puede cambiar la ampliación de cada panel utilizando el **Magnify** herramienta en el **Editor de imágenes** barra de herramientas o mediante las teclas de aceleración.

Puede ampliar el panel menor de la **Editor de imágenes** ventana y usar los dos paneles para mostrar diferentes regiones de una imagen grande. Seleccione esta opción dentro del panel para elegirlo.

Puede cambiar el tamaño relativo de los paneles colocando el puntero en la barra de división y al mover la barra de división hacia la izquierda o derecha. Si desea trabajar en un solo panel, puede mover la barra de división a ambos lados.

Si el **Editor de imágenes** panel es ampliada por un factor de 4 o mayor, puede mostrar una cuadrícula de píxeles que delimita los píxeles individuales de la imagen.

### <a name="to-change-the-magnification-factor"></a>Para cambiar el factor de ampliación

De forma predeterminada, el **Editor de imágenes** muestra la vista en el panel izquierdo al tamaño real y la vista en el panel derecho a 6 veces el tamaño real. El factor de ampliación (que se muestra en la barra de estado en la parte inferior del área de trabajo) es la relación entre el tamaño real de la imagen y el tamaño de muestra. El factor de forma predeterminada es 6 y el intervalo es de 1 a 10.

1. Seleccione el **Editor de imágenes** panel cuyo factor de ampliación que desee cambiar.

1. En el **Editor de imágenes** barra de herramientas, seleccione la flecha situada a la derecha de la **Magnify** de herramientas y seleccione el factor de ampliación desde el submenú: **1 X**, **2 X**, **6 X**, o **8 X**.

   > [!NOTE]
   > Para seleccionar un factor de ampliación que no aparecen en la **Magnify** herramienta, utilice las teclas de aceleración.

### <a name="to-display-or-hide-the-pixel-grid"></a>Para mostrar u ocultar la cuadrícula de píxeles

Para todos los **Editor de imágenes** paneles con un factor de ampliación de 4 o superior, puede mostrar una cuadrícula que delimita los píxeles individuales de la imagen.

1. Vaya al menú **imagen** > **configuración de la cuadrícula**.

1. Seleccione el **cuadrícula de píxeles** casilla de verificación para mostrar la cuadrícula, o desactive la casilla para ocultar la cuadrícula.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>

<!--[Icons](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)-->
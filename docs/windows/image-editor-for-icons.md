---
title: Editor de imágenes para iconosC++()
ms.date: 02/15/2019
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.icon
- vc.editors.texttool
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
ms.openlocfilehash: 47798b5d628484482dffdc963d6e8c7a809f42ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168021"
---
# <a name="image-editor-for-icons-c"></a>Editor de imágenes para iconosC++()

Al seleccionar un archivo de imagen (por ejemplo,. ico,. bmp,. png) en **Explorador de soluciones**, la imagen se abre en el **Editor de imágenes** del mismo modo que los archivos de código se abren en el editor de **código**. Cuando está activa una pestaña del **Editor de imágenes** , verá barras de herramientas con muchas herramientas para crear y editar imágenes. Junto con los mapas de bits, los iconos y los cursores, puede editar imágenes en formato GIF o JPEG mediante los comandos del menú **imagen** y las herramientas de la barra de herramientas del **Editor de imágenes** .

Los recursos gráficos son las imágenes que define para la aplicación. Puede dibujar a mano alzada o dibujar con formas. Puede seleccionar partes de una imagen para editarlas, voltearlas o cambiar su tamaño, o puede crear un pincel personalizado a partir de una parte seleccionada de una imagen y dibujar con ese pincel. Puede definir las propiedades de la imagen, guardar las imágenes en diferentes formatos y convertir las imágenes de un formato a otro.

> [!NOTE]
> Con el **Editor de imágenes**, puede ver imágenes de 32 bits, pero no puede modificarlas.

También puede usar el **Editor de imágenes** y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

Además de crear nuevos recursos gráficos, puede [importar imágenes existentes](../windows/how-to-copy-resources.md#import-and-export-resources) para editarlas y agregarlas a su proyecto. También puede abrir y editar imágenes que no forman parte de un proyecto para la [edición independiente de imágenes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

Para obtener información sobre el **Editor de imágenes**, consulte [creación de un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), edición de una [imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [uso de una herramienta de dibujo](../windows/using-a-drawing-tool-image-editor-for-icons.md), [trabajo con colores](../windows/working-with-color-image-editor-for-icons.md)y [teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Descargue sin costo la **biblioteca de imágenes de Visual Studio** que contiene muchas animaciones, mapas de bits e iconos que puede usar en sus aplicaciones. Para obtener más información sobre cómo descargar la biblioteca, vea la [biblioteca de imágenes de Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Imagen (Menú)

El menú **imagen** , que solo aparece cuando el **Editor de imágenes** está activo, tiene comandos para editar imágenes, administrar paletas de colores y establecer opciones de la ventana del **Editor de imágenes** . Además, los comandos para usar imágenes de dispositivo están disponibles cuando se trabaja con iconos y cursores.

|Get-Help|Descripción|
|---|---|
|**Invertir colores**|Invierte los colores.|
|**Voltear horizontalmente**|Voltea la imagen o la selección en sentido horizontal.|
|**Voltear verticalmente**|Voltea la imagen o la selección en sentido vertical.|
|**Girar 90 grados**|Gira la imagen o la selección 90 grados.|
|**Ventana mostrar colores**|Abre la ventana **colores** , en la que puede elegir los colores que se usarán para la imagen.|
|**Usar la selección como pincel**|Permite crear un pincel personalizado a partir de una parte de una imagen.<br/><br/>La selección se convierte en un pincel personalizado que distribuye los colores de la selección a través de la imagen. Las copias de la selección se quedan a lo largo del trazado de arrastre. Cuanto más lentamente arrastre, más copias se realizarán.|
|**Selección de copiar y esquematizar**|Crea una copia de la selección actual y la resalta.<br/><br/>Si el color de fondo está contenido en la selección actual, se excluirá si se selecciona transparente.
|**Ajustar colores**|Abre el **selector de colores personalizado**, que le permite personalizar los colores que usa para la imagen.|
|**Cargar paleta**|Abre el cuadro de diálogo **paleta de colores de carga** , que permite cargar los colores de la paleta guardados previamente en un archivo. PAL.|
|**Guardar paleta**|Guarda los colores de la paleta en un archivo. PAL.|
|**Dibujar opaco**|Cuando se selecciona, hace que la selección actual sea opaca.<br/><br/>Cuando está desactivada, hace que la selección actual sea transparente.|
|**Editor de barras de herramientas**|Abre el [cuadro de diálogo nuevo recurso](../windows/new-toolbar-resource-dialog-box.md)de la barra de herramientas.|
|**Configuración de la cuadrícula**|Abre el cuadro de diálogo Configuración de la **cuadrícula** en el que puede especificar cuadrículas para la imagen.|
|**Nuevo tipo de imagen**|Abre el [cuadro de diálogo nuevo \<dispositivo > tipo de imagen](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Un recurso de icono único puede contener varias imágenes de diferentes tamaños y Windows puede usar el tamaño de icono adecuado en función de cómo se vaya a mostrar. Un nuevo tipo de dispositivo no modifica el tamaño del icono, sino que crea una nueva imagen dentro del icono. Solo se aplica a los iconos y cursores.|
|**Icono actual/tipo de imagen de cursor**|Abre un submenú que muestra las nueve primeras imágenes de cursor o icono disponibles. El último comando del submenú, **más**, abre el [cuadro de diálogo abrir \<dispositivo > imagen](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Eliminar tipo de imagen**|Elimina la imagen de dispositivo seleccionada.|
|**Herramientas**|Inicia un submenú que contiene todas las herramientas disponibles en la barra de herramientas del **Editor de imágenes** .|

El cuadro de diálogo Configuración de la **cuadrícula** permite especificar la configuración de la cuadrícula para la imagen y mostrar las líneas de cuadrícula sobre la imagen modificada. Las líneas son útiles para editar la imagen, pero no se guardan como parte de la propia imagen.

|Propiedad|Descripción|
|---|---|
|**Cuadrícula de píxeles**|Cuando esta opción está activada, muestra una cuadrícula alrededor de cada píxel en el **Editor de imágenes**.<br/><br/>La cuadrícula solo aparece en 4 × y resoluciones superiores.|
|**Cuadrícula de mosaico**|Cuando está seleccionada, muestra una cuadrícula alrededor de los bloques de píxeles en el **Editor de imágenes**, especificados por los valores de espaciado de la cuadrícula.|
|**Width**|Especifica el ancho de cada bloque de mosaico.<br/><br/>Esta propiedad es útil cuando se dibujan mapas de bits que contienen varias imágenes que se organizan a intervalos regulares.|
|**Height**|Especifica el alto de cada bloque de mosaico.<br/><br/>Esta propiedad es útil cuando se dibujan mapas de bits que contienen varias imágenes que se organizan a intervalos regulares.|

## <a name="toolbar"></a>Barra de herramientas

La barra de herramientas del **Editor de imágenes** contiene herramientas para dibujar, pintar, escribir texto, borrar y manipular vistas. También contiene un selector de opciones, con el que puede seleccionar opciones para usar cada herramienta. Por ejemplo, puede elegir entre varios anchos de pincel, factores de ampliación y estilos de línea.

Todas las herramientas disponibles en la barra de herramientas del **Editor de imágenes** también están disponibles en la **imagen** de menú > **herramientas**. Para usar la barra de herramientas del **Editor de imágenes** y el selector de **Opciones** , seleccione la herramienta o la opción que desee.

![Barra de herramientas del editor de imágenes](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
Barra de herramientas del **Editor de imágenes**

> [!TIP]
> La información sobre herramientas aparece cuando desplaza el cursor sobre un botón de la barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

Dado que muchas de las herramientas de dibujo están disponibles desde el [teclado](../windows/accelerator-keys-image-editor-for-icons.md), a veces resulta útil ocultar la barra de herramientas del **Editor de imágenes** .

- Para mostrar u ocultar la barra de herramientas del **Editor de imágenes** , vaya a la **vista** de menú > **barras de herramientas** y elija editor de **imágenes**.

> [!NOTE]
> Los elementos de esta barra de herramientas no estarán disponibles cuando un archivo de imagen del proyecto o la solución actual no esté abierto en el **Editor de imágenes**.

### <a name="option-selector"></a>selector de opciones

Con el selector de **Opciones** puede especificar el ancho de una línea, trazo de pincel, etc. El icono del botón del selector de **Opciones** cambia en función de la herramienta que haya seleccionado.

![Dibujar&#45;el selector de formas en la barra de herramientas del editor de imágenes](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
Selector de **Opciones** de la barra de herramientas del **Editor de imágenes**

### <a name="text-tool"></a>Herramienta de texto

Utilice el cuadro de diálogo **herramienta de texto** para agregar texto a un recurso de cursor, mapa de bits o icono.

Para obtener acceso a este cuadro de diálogo, abra el **Editor de imágenes** y vaya a la **imagen** de menú > **herramientas**y, a continuación, seleccione el comando de la **herramienta texto** .

> [!TIP]
> Puede hacer clic con el botón secundario en el cuadro de diálogo **herramienta de texto** para tener acceso a un menú contextual predeterminado que contiene una lista de comandos de Windows estándar.

Abra el cuadro de diálogo **fuente de herramienta de texto** para cambiar la fuente, el estilo o el tamaño de la fuente del cursor. Los cambios se aplican al texto que se muestra en el área de **texto** .

Para obtener acceso a este cuadro de diálogo, seleccione el botón **fuente** en el cuadro de diálogo **herramienta de texto** . Las propiedades disponibles son:

|Propiedad|Descripción|
|---|---|
|**Fuente**|Muestra las fuentes disponibles.|
|**Estilo de fuente**|Muestra los estilos disponibles para la fuente especificada.|
|**Tamaño**|Muestra los tamaños de punto disponibles para la fuente especificada.|
|**Ejemplo**|Muestra un ejemplo de cómo aparecerá el texto con la configuración de fuente especificada.|
|**Script**|Muestra los scripts de idioma disponibles para la fuente especificada.<br/><br/>Al seleccionar un script de idioma diferente, el juego de caracteres de ese idioma está disponible para la creación de documentos multilingües.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Para cambiar la fuente de texto de una imagen

Este es un ejemplo de cómo agregar texto a un icono en una aplicación de Windows y manipular la fuente del texto.

1. Cree una C++ aplicación Windows Forms. Para obtener más información, consulte [Cómo: crear aplicaciones Windows Forms](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90)). De forma predeterminada, se agrega un archivo *app. ico* al proyecto.

1. En **Explorador de soluciones**, haga doble clic en el archivo *app. ico*. Se abrirá el **Editor de imágenes** .

1. Vaya a menú **imagen** > **herramientas** y seleccione **herramienta de texto**.

1. En el cuadro de diálogo **herramienta** de texto *C++* , escriba en el área de texto vacía. Este texto aparecerá en un cuadro de tamaño variable situado en la esquina superior izquierda de *app. ico* en el **Editor de imágenes**.

1. En el **Editor de imágenes**, arrastre el cuadro redimensionable hasta el centro de *app. ico* para mejorar la legibilidad del texto.

1. En el cuadro de diálogo **herramienta de texto** , seleccione el botón **fuente** .

1. En el cuadro de diálogo **fuente de herramienta de texto** :

   - Seleccione **Times New Roman** en la lista de fuentes disponibles que aparecen en el cuadro de lista **fuente** .

   - Seleccione **negrita** en la lista de estilos de fuente disponibles que aparecen en el cuadro de lista **estilo de fuente** .

   - Seleccione **10** en la lista de tamaños de puntos disponibles que aparecen en el cuadro de lista **tamaño** .

   - Elija **Aceptar**. Se cerrará el cuadro de diálogo **fuente de herramienta de texto** y se aplicará la nueva configuración de fuente al texto.

1. Elija **cerrar** en el cuadro de diálogo **herramienta de texto** . El cuadro de tamaño variable alrededor del texto desaparecerá del **Editor de imágenes**.

El área de texto muestra el texto que aparece como parte del recurso. Inicialmente, esta área está vacía.

> [!NOTE]
> Si se establece el **fondo transparente** , solo se colocará el texto en la imagen. Si se establece el **fondo opaco** , se colocará detrás del texto un rectángulo delimitador, rellenado con el color de fondo.

## <a name="window-panes"></a>Paneles de la ventana

La ventana del **Editor de imágenes** muestra dos vistas de una imagen, con una barra de división que separa los dos paneles. Se puede arrastrar dicha barra a uno u otro lado para cambiar el tamaño relativo de los paneles. El panel activo muestra un borde de selección.

Una vista es el tamaño real y la otra se amplía mediante un factor de ampliación predeterminado de 6. Las vistas de estos dos paneles se actualizan automáticamente, los cambios que se realicen en un panel se muestran inmediatamente en el otro. Los dos paneles facilitan el trabajo en una vista ampliada de la imagen, en la que puede distinguir píxeles individuales y, al mismo tiempo, observar el efecto del trabajo en la vista de tamaño real de la imagen.

En el panel izquierdo se usa tanto espacio como sea necesario (hasta la mitad de la ventana de **imagen** ) para mostrar la vista de ampliación 1:1 predeterminada de la imagen. En el panel derecho se muestra una imagen con zoom de ampliación de 6:1 predeterminada. Puede cambiar la ampliación en cada panel mediante la herramienta **aumentar** en la barra de herramientas del **Editor de imágenes** o con las teclas de aceleración.

Puede ampliar el panel más pequeño de la ventana del **Editor de imágenes** y usar los dos paneles para mostrar diferentes regiones de una imagen grande. Seleccione dentro del panel para seleccionarlo.

Puede cambiar los tamaños relativos de los paneles colocando el puntero en la barra de división y moviendo la barra de división a la derecha o a la izquierda. La barra de división puede moverse hasta cualquier lado si desea trabajar solo en un panel.

Si el panel del **Editor de imágenes** se amplía mediante un factor de 4 o superior, puede mostrar una cuadrícula de píxeles que delimita los píxeles individuales de la imagen.

### <a name="to-change-the-magnification-factor"></a>Para cambiar el factor de ampliación

De forma predeterminada, el **Editor de imágenes** muestra la vista en el panel izquierdo en tamaño real y la vista en el panel derecho a 6 veces el tamaño real. El factor de ampliación (que aparece en la barra de estado en la parte inferior del área de trabajo) es la proporción entre el tamaño real de la imagen y el tamaño mostrado. El factor predeterminado es 6 y el intervalo está comprendido entre 1 y 10.

1. Seleccione el panel del **Editor de imágenes** cuyo factor de ampliación desea cambiar.

1. En la barra de herramientas del **Editor de imágenes** , seleccione la flecha situada a la derecha de la herramienta **aumentar** y seleccione el factor de ampliación en el submenú: **1x**, **2x**, **6X**o **8X**.

   > [!NOTE]
   > Para seleccionar un factor de ampliación distinto de los enumerados en la herramienta **aumentar** , use las teclas de aceleración.

### <a name="to-display-or-hide-the-pixel-grid"></a>Para mostrar u ocultar la cuadrícula de píxeles

En todos los paneles del **Editor de imágenes** con un factor de ampliación de 4 o superior, puede mostrar una cuadrícula que delimita los píxeles individuales de la imagen.

1. Vaya a la **imagen** de menú > configuración de la **cuadrícula**.

1. Active la casilla **cuadrícula de píxeles** para mostrar la cuadrícula o desactive la casilla para ocultar la cuadrícula.

## <a name="requirements"></a>Requisitos

None

## <a name="see-also"></a>Consulte también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Iconos](/windows/win32/menurc/icons)

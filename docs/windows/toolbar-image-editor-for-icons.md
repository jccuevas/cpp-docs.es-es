---
title: Barra de herramientas (Editor de C++ imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
helpviewer_keywords:
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
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
ms.openlocfilehash: dfbd721afd997f3151b1c20a7e0e1fb60e0c83e4
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560327"
---
# <a name="toolbar-c-image-editor-for-icons"></a>Barra de herramientas (Editor de C++ imágenes para iconos)

El **Editor de imágenes** barra de herramientas contiene herramientas de dibujo, pintura, escribir texto, borrado y manipulación de vistas. También contiene un selector de opciones, con el que puede seleccionar opciones para usar cada herramienta. Por ejemplo, puede elegir desde diversos anchos de pincel, factores de ampliación y estilos de línea.

> [!NOTE]
> Todas las herramientas disponibles en el **Editor de imágenes** también están disponibles en la barra de herramientas del **imagen** menú (bajo la **herramientas** comando).

![Barra de herramientas del Editor de imágenes](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") barra de herramientas del Editor de imágenes

Para usar el **Editor de imágenes** barra de herramientas y **opción** selector, seleccione la herramienta o la opción que desee.

> [!TIP]
> Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

Con el **opción** selector se puede especificar el ancho de una línea, el trazo de pincel y mucho más. En el icono del **opción** cambios de botón de selector según la herramienta que ha seleccionado.

![Dibujo&#45;selector con forma de la barra de herramientas del Editor de imágenes](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") Selector de opciones en la barra de herramientas del Editor de imágenes

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="use-the-text-tool-dialog-box"></a>Utilice el cuadro de diálogo Herramienta de texto

Use la **texto herramienta** cuadro de diálogo para agregar texto a un recurso de cursor, mapa de bits o icono.

Para obtener acceso a este cuadro de diálogo, abra el [Editor de imágenes](../windows/window-panes-image-editor-for-icons.md). Seleccione **herramientas** desde el **imagen** menú y, a continuación, seleccione el **texto herramienta** comando.

### <a name="font-button"></a>Botón de fuente

Se abre el **fuente de herramienta de texto** cuadro de diálogo, en el que puede cambiar la fuente, estilo o tamaño de la fuente del cursor. Los cambios se aplican al texto que se muestra en el **texto** área.

Para obtener acceso a este cuadro de diálogo, seleccione el **fuente** situado en la **texto herramienta** cuadro de diálogo. Las propiedades disponibles son:

|Property|Descripción|
|---|---|
|**Fuente**|Enumera las fuentes disponibles.|
|**Estilo de fuente**|Se enumeran los estilos disponibles para la fuente especificada.|
|**Size**|Enumera los tamaños de punto disponibles para la fuente especificada.|
|**Ejemplo**|Muestra un ejemplo de cómo aparecerá el texto con la configuración de fuente especificado.|
|**Script**|Enumera las secuencias de comandos de idioma disponibles para la fuente especificada. Cuando se selecciona un script de idioma diferente, el juego de caracteres para ese idioma estará disponible para la creación de documentos en varios idiomas.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Para cambiar la fuente del texto de una imagen

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

### <a name="text-area"></a>Área de texto

Muestra el texto que aparece como parte del recurso. Inicialmente, esta área está vacía.

> [!NOTE]
> Si **fondo transparente** está establecido, sólo el texto se colocará en la imagen. Si **fondo opaco** está establecido, un rectángulo delimitador, relleno con el [color de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), se colocarán detrás del texto. Para obtener más información, consulte [elegir opaco y fondos transparentes](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Puede haga doble clic en el **texto herramienta** cuadro de diálogo para tener acceso a un menú contextual predeterminado que contiene una lista de comandos de Windows estándar.

## <a name="to-display-or-hide-the-image-editor-toolbar"></a>Para mostrar u ocultar la barra de herramientas del Editor de imágenes

Puesto que muchas de las herramientas de dibujo están disponibles desde el [teclado](../windows/accelerator-keys-image-editor-for-icons.md), a veces resulta útil ocultar el **Editor de imágenes** barra de herramientas.

En el **vista** menú, seleccione **las barras de herramientas** , a continuación, elija **Editor de imágenes**.

   > [!NOTE]
   > Los elementos de esta barra de herramientas aparecerán no están disponibles cuando un archivo de imagen del proyecto actual o la solución no está abierta en el **Editor de imágenes**. Consulte [creación de un icono o imagen otras](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), para obtener información sobre cómo agregar archivos de imagen a sus proyectos.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Ventana colores](../windows/colors-window-image-editor-for-icons.md)<br/>
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
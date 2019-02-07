---
title: Menú imagen (Editor de C++ imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
helpviewer_keywords:
- Image menu
- Grid Settings dialog box [C++]
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
ms.openlocfilehash: e7d7d92401d5910cbb8aba8ab4c6000eca45cb01
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849735"
---
# <a name="image-menu-c-image-editor-for-icons"></a>Menú imagen (Editor de C++ imágenes para iconos)

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

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Cambiar el tamaño de una imagen](../windows/resizing-an-image-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)
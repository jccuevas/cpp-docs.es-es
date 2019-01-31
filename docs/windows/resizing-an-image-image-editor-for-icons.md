---
title: Cambiar el tamaño de una imagen (Editor de imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
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
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: d88a4cccff5b9b7b6303329782b7367cb953b13d
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484973"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Cambiar el tamaño de una imagen (Editor de imágenes para iconos)

El comportamiento de la **imagen** editor al cambiar el tamaño de una imagen depende de si ha [seleccionado](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) la imagen completa o sólo una parte del mismo.

Cuando la selección incluye sólo una parte de la imagen, el **imagen** editor reduce la selección, eliminación de filas o columnas de píxeles y rellenando las vacantes regiones con el color de fondo actual. También puede ampliar la selección al duplicar filas o columnas de píxeles.

Cuando la selección incluye toda la imagen, el **imagen** editor bien reduce y expande la imagen, o se recorta y lo amplía.

Hay dos mecanismos para cambiar el tamaño de una imagen: los controladores de tamaño y la [ventana propiedades](/visualstudio/ide/reference/properties-window). Arrastre los controladores de tamaño para cambiar el tamaño de todo o parte de una imagen. Ajuste de tamaño que se pueden arrastrar son sólidos. No puede arrastrar cuadros huecos. Use la **propiedades** ventana para cambiar el tamaño de toda la imagen solo, no es una parte seleccionada.

![Controladores en un mapa de bits de tamaño](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Asas de ajuste de tamaño

> [!NOTE]
> Si tiene la **cuadrícula de mosaico** opción seleccionada en el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md), a continuación, cambiar el tamaño se ajusta a la siguiente línea de cuadrícula de mosaico. Si solo el **cuadrícula de píxeles** opción está seleccionada (el valor predeterminado), el cambio de tamaño se ajusta a la siguiente píxel disponible.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-resize-an-entire-image-using-the-properties-window"></a>Para cambiar el tamaño de una imagen completa mediante la ventana Propiedades

1. Abra la imagen cuyas propiedades desea cambiar.

1. En el **ancho** y **alto** cuadros en el [ventana propiedades](/visualstudio/ide/reference/properties-window), escriba las dimensiones que desee.

   Si va a aumentar el tamaño de la imagen, el **imagen** editor amplía la imagen a la derecha, hacia abajo, o ambos y rellena la nueva región con el color de fondo actual. La imagen no quede estirada.

   Si reduce el tamaño de la imagen, el **imagen** editor recorta la imagen en el borde derecho o inferior, o ambos.

   > [!NOTE]
   > Puede usar el **ancho** y **alto** propiedades para cambiar el tamaño de la imagen completa no para cambiar el tamaño de una selección parcial.

## <a name="to-crop-or-extend-an-entire-image"></a>Para recortar o ampliar una imagen completa

1. Seleccione toda la imagen.

   Si parte de la imagen está seleccionado actualmente y que desea seleccionar toda la imagen, seleccione cualquier parte de la imagen fuera del borde de selección actual.

1. Arrastre un controlador de tamaño hasta que la imagen es el tamaño correcto.

Normalmente, el **imagen** editor recorta o amplía una imagen cuando cambia el tamaño al mover un controlador de tamaño. Si mantiene presionada la **MAYÚS** clave como mover un controlador de tamaño, el **imagen** editor reduce o expande la imagen.

## <a name="to-shrink-or-stretch-an-entire-image"></a>Para comprimir o ajustar una imagen completa

1. Seleccione toda la imagen.

   Si una parte de la imagen está seleccionada actualmente y que desea seleccionar toda la imagen, seleccione cualquier parte de la imagen fuera del borde de selección actual.

1. Mantenga presionada la **MAYÚS** clave y arrastre un controlador de tamaño hasta que la imagen es el tamaño correcto.

## <a name="to-shrink-or-stretch-part-of-an-image"></a>Para comprimir o expandir parte de una imagen

1. Seleccione la parte de la imagen que desea cambiar el tamaño. Para obtener más información, consulte [seleccionar un área de la imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Arrastre uno de los controladores de tamaño hasta que la selección es el tamaño correcto.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)
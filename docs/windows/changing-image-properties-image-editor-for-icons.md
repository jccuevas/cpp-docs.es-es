---
title: Cambiar propiedades de la imagen (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3b85faff95e3053ea46edcedef7443cdab445d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422238"
---
# <a name="changing-image-properties-image-editor-for-icons"></a>Cambiar las propiedades de la imagen (Editor de imágenes para iconos)

Puede establecer o modificar las propiedades de una imagen mediante la [ventana propiedades](/visualstudio/ide/reference/properties-window).

### <a name="to-change-an-images-properties"></a>Para cambiar las propiedades de una imagen

1. Abra la imagen en el **imagen** editor.

2. En el **propiedades** ventana, cambie cualquiera o todas las propiedades para la imagen.

   |Property|Descripción|
   |--------------|-----------------|
   |**Colores**|Especifica la combinación de colores para la imagen. Seleccione **monocromático**, **16**, o **256**, o **Color verdadero**. Si se ha dibujado la imagen con una paleta de colores de 16, si selecciona **monocromático** hace que las sustituciones de blanco y negro para los colores en la imagen. No se mantiene siempre contraste: por ejemplo, las áreas adyacentes de color rojo y verde se ambos convierten a negro.|
   |**Nombre de archivo**|Especifica el nombre del archivo de imagen. De forma predeterminada, Visual Studio asigna un nombre de archivo base creado mediante la eliminación de los primeros cuatro caracteres ("IDB_") desde el identificador de recursos predeterminado (IDB_BITMAP1) y agregando la extensión adecuada. El nombre de archivo para la imagen en este ejemplo sería `BITMAP1.bmp`. Puede cambiar el nombre `MYBITMAP1.bmp`.|
   |**Alto**|Establece el alto de la imagen (en píxeles). El valor predeterminado es 48. La imagen se recorta o se agrega espacio en blanco debajo de la imagen existente.|
   |**ID**|Establece el identificador de recursos. Para una imagen, Microsoft Visual Studio, de forma predeterminada, asigna el siguiente identificador disponible en una serie: IDB_BITMAP1, IDB_BITMAP2, y así sucesivamente. Se usan nombres similares para iconos y cursores.|
   |**Paleta**|Cambia las propiedades de color. Haga doble clic para seleccionar un color y mostrar el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Definir el color escribiendo los valores RGB o HSL en los cuadros de texto correspondientes.|
   |**SaveCompressed**|Indica si la imagen está en un formato comprimido. Esta propiedad es de sólo lectura. Visual Studio no permite guardar imágenes en un formato comprimido, por lo que las imágenes creadas en Visual Studio, esta propiedad será **False**. Si abre una imagen comprimida (creada en otro programa) en Visual Studio, esta propiedad será **True**. Si guarda una imagen comprimida con Visual Studio, se descomprimen y esta propiedad se restablecerá a **False**.|
   |**Ancho**|Establece el ancho de la imagen (en píxeles). El valor predeterminado para los mapas de bits es 48. La imagen se recorta o espacio en blanco se agrega a la derecha de la imagen existente.|

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)
---
title: "Cambiar propiedades de la imagen (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Image editor [C++], image properties
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96122b2bdc6419b41cd0e00cb544955d8d7c8463
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="changing-image-properties-image-editor-for-icons"></a>Cambiar las propiedades de la imagen (Editor de imágenes para iconos)
Puede establecer o modificar las propiedades de una imagen mediante la [ventana propiedades](/visualstudio/ide/reference/properties-window).  
  
### <a name="to-change-an-images-properties"></a>Para cambiar las propiedades de una imagen  
  
1.  Abrir la imagen en el **imagen** editor.  
  
2.  En el **propiedades** ventana, cambiar alguna o todas las propiedades de la imagen.  
  
    |Property|Descripción|  
    |--------------|-----------------|  
    |**Colores**|Especifica la combinación de colores de la imagen. Seleccione monocromático, 16, 256 o True Color. Si ya ha dibujado la imagen con una paleta de colores de 16, selección de Monocromático causa sustituciones de blanco y negro para los colores en la imagen. No se mantiene siempre contraste: por ejemplo, adyacentes áreas de color rojo y verde se ambos convierten en negro.|  
    |**Nombre de archivo**|Especifica el nombre del archivo de imagen. De manera predeterminada, Visual Studio asigna un nombre de archivo base que se creó mediante la eliminación de los primeros cuatro caracteres ("IDB_") desde el identificador de recursos predeterminado (IDB_BITMAP1) y agregando la extensión correspondiente. El nombre de archivo para la imagen en este ejemplo sería BITMAP1.bmp. Se puede cambiar este nombre a MIBITMAP1.bmp.|  
    |**Alto**|Establece el alto de la imagen (en píxeles). El valor predeterminado es 48. La imagen se recorta o se agrega espacio en blanco debajo de la imagen existente.|  
    |**ID**|Establece el identificador de recursos. Para una imagen, Microsoft Visual Studio, de forma predeterminada, asigna el siguiente identificador disponible de una serie: IDB_BITMAP1, IDB_BITMAP2, y así sucesivamente. Se usan nombres similares para los iconos y cursores.|  
    |**Paleta**|Cambia las propiedades del color. Haga doble clic para seleccionar un color y mostrar el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Definir el color escribiendo los valores RGB o HSL en los cuadros de texto correspondientes.|  
    |**SaveCompressed**|Indica si la imagen está en un formato comprimido. Esta propiedad es de sólo lectura. Visual Studio no permite guardar imágenes en un formato comprimido, por lo que para cualquier imagen creada en Visual Studio, esta propiedad será **False**. Si abre una imagen comprimida (creada en otro programa) en Visual Studio, esta propiedad será **True**. Si guarda una imagen comprimida con Visual Studio, se descomprimirá y esta propiedad se restablecerá **False**.|  
    |**Ancho**|Establece el ancho de la imagen (en píxeles). El valor predeterminado para los mapas de bits es 48. La imagen se recorta o espacio en blanco se agrega a la derecha de la imagen existente.|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)


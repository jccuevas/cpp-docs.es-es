---
title: Cambiar el tamaño de una imagen (Editor de imágenes para iconos) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c6636e1f92907c301c6e66abd63f744375bffeb8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Cambiar el tamaño de una imagen (Editor de imágenes para iconos)
El comportamiento del editor de imágenes al cambiar el tamaño de una imagen depende de si ha [seleccionado](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) la imagen completa o sólo una parte del mismo.  
  
 Si la selección incluye sólo una parte de la imagen, el editor de imágenes reduce la selección mediante la eliminación de filas o columnas de píxeles y rellenando las regiones vaciadas con el color de fondo actual, o bien se expande la selección duplicando filas o columnas de píxeles.  
  
 Si la selección incluye toda la imagen, el editor de imágenes ya sea se reduce y expande la imagen, o se recorta y lo extiende.  
  
 Hay dos mecanismos para cambiar el tamaño de una imagen: los controladores de tamaño y la [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede arrastrar los controladores de tamaño para cambiar el tamaño de todo o parte de una imagen. Controladores de tamaño que se pueden arrastrar estén firmes. No puede arrastrar cuadros huecos. Puede usar la ventana de propiedades para cambiar el tamaño de la imagen completa, no un elemento seleccionado.  
  
 ![Controladores en un mapa de bits de tamaño](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Asas de ajuste de tamaño  
  
> [!NOTE]
>  Si tiene la opción de cuadrícula de mosaico seleccionada en el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md), a continuación, cambiar el tamaño se ajusta a la siguiente línea de cuadrícula de mosaico. Si sólo la cuadrícula de píxeles opción está activada (valor predeterminado), el cambio de tamaño se ajusta al siguiente píxel disponible.  
  
-   [Cambiar el tamaño de una imagen completa](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Recortar o ampliar una imagen completa](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Comprimir o expandir una imagen completa](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Comprimir o expandir parte de una imagen](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)


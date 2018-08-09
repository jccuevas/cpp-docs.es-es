---
title: Cambiar el tamaño de una imagen (Editor de imágenes para iconos) | Microsoft Docs
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
ms.openlocfilehash: 9c972f4038da4b4ed1d52fee0b8029b6f48ff3bb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013878"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Cambiar el tamaño de una imagen (Editor de imágenes para iconos)
El comportamiento de la **imagen** editor al cambiar el tamaño de una imagen depende de si ha [seleccionado](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) la imagen completa o sólo una parte del mismo.  
  
 Cuando la selección incluye sólo una parte de la imagen, el **imagen** editor reduce la selección, eliminación de filas o columnas de píxeles y rellenando las vacantes regiones con el color de fondo actual, o expande la selección por duplicar filas o columnas de píxeles.  
  
 Cuando la selección incluye toda la imagen, el **imagen** editor bien reduce y expande la imagen, o se recorta y lo amplía.  
  
 Hay dos mecanismos para cambiar el tamaño de una imagen: los controladores de tamaño y la [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede arrastrar los controladores de tamaño para cambiar el tamaño de todo o parte de una imagen. Ajuste de tamaño que se pueden arrastrar son sólidos. No puede arrastrar cuadros huecos. Puede usar el **propiedades** ventana para cambiar el tamaño de toda la imagen solo, no es una parte seleccionada.  
  
 ![Controladores en un mapa de bits de tamaño](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Asas de ajuste de tamaño  
  
> [!NOTE]
>  Si tiene la **cuadrícula de mosaico** opción seleccionada en el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md), a continuación, cambiar el tamaño se ajusta a la siguiente línea de cuadrícula de mosaico. Si solo el **cuadrícula de píxeles** opción está seleccionada (el valor predeterminado), el cambio de tamaño se ajusta a la siguiente píxel disponible.  
  
-   [Cambiar el tamaño de una imagen completa](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Recortar o ampliar una imagen completa](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Comprimir o ajustar una imagen completa](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Comprimir o expandir parte de una imagen](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)
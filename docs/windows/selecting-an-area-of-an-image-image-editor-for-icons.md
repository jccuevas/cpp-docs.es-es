---
title: "Seleccionar un área de una imagen (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3060c47af46a39358ac2e8a7ab5b573f50867869
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>Seleccionar un área de una imagen (Editor de imágenes para iconos)
Puede usar herramientas de selección para definir un área de una imagen que desee cortar, copiar, borrar, cambiar el tamaño, invertir o mover. Con el **selección del rectángulo** herramienta puede definir y seleccionar una región rectangular de la imagen. Con el **selección Irregular** herramienta puede dibujar un mano alzada el contorno del área que desea seleccionar para el cortar, copiar u otra operación.  
  
> [!NOTE]
>  Consulte la **rectángulo de selección** y **selección Irregular** herramientas se ilustran en [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o ver la información sobre herramientas asociado a cada botón en la **Editor de imágenes** barra de herramientas.  
  
 También puede crear un pincel personalizado de una selección. Para obtener más información, consulte [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
### <a name="to-select-an-area-of-an-image"></a>Para seleccionar un área de una imagen  
  
1.  En el **Editor de imágenes** barra de herramientas (o desde el **imagen** menú, **herramientas** comandos), haga clic en la herramienta de selección que desee.  
  
2.  Mover el punto de inserción a una de las esquinas del área de imagen que desea seleccionar. Cruz aparece cuando el punto de inserción está sobre la imagen.  
  
3.  Arrastre el punto de inserción hasta la esquina opuesta del área que desea seleccionar. Un rectángulo muestra los píxeles que se seleccionarán. Todos los píxeles dentro del rectángulo, las de rectángulo, incluidas se incluyen en la selección.  
  
4.  Suelte el botón del mouse. El borde de selección rodea el área seleccionada.  
  
### <a name="to-select-an-entire-image"></a>Para seleccionar una imagen completa  
  
1.  Haga clic en la imagen fuera de la selección actual. El borde de selección cambia el foco y abarca toda la imagen de nuevo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)


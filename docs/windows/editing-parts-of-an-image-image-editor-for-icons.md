---
title: "Editar partes de una imagen (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: acd4859bf7c80cf2bbe6cd2d86c39d0fc596351d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Editar partes de una imagen (Editor de imágenes para iconos)
Puede realizar operaciones de edición estándares, cortar, copiar, borrar y mover: en un [selección](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), si la selección es la imagen completa o solamente una parte de ella. Dado que el editor de imágenes utiliza el Portapapeles de Windows, pueden transferirse imágenes entre el editor de imágenes y otras aplicaciones para Windows.  
  
 Además, puede cambiar la selección, si incluye toda la imagen o solo una parte.  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Cortar la selección actual y colocarlo en el Portapapeles  
  
1.  Haga clic en **cortar** en el **editar** menú.  
  
### <a name="to-copy-the-selection"></a>Para copiar la selección  
  
1.  Coloque el puntero dentro del borde de selección o en cualquier lugar en él excepto los controladores de tamaño.  
  
2.  Mantenga presionada la **CTRL** clave mientras arrastra la selección a una nueva ubicación. El área de la selección original se ha modificado.  
  
3.  Para copiar la selección en la imagen en su ubicación actual, haga clic fuera del cursor de selección.  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Para pegar el contenido del Portapapeles en una imagen  
  
1.  Desde el **editar** menú, elija **pegar**.  
  
     El contenido del Portapapeles, rodeado por el borde de selección, aparece en la esquina superior izquierda del panel.  
  
2.  Coloque el puntero dentro del borde de selección y arrastre la imagen a la ubicación deseada en la imagen.  
  
3.  Para fijar la imagen en su nueva ubicación, haga clic fuera del borde de selección.  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Para eliminar la selección actual sin moverlo en el Portapapeles  
  
1.  Desde el **editar** menú, elija **eliminar**.  
  
     La zona original de la selección se rellena con el color de fondo actual.  
  
    > [!NOTE]
    >  Puede tener acceso a cortar, copiar, pegar y eliminar comandos haciendo clic en la ventana Vista de recursos.  
  
### <a name="to-move-the-selection"></a>Para mover la selección  
  
1.  Coloque el puntero dentro del borde de selección o en cualquier lugar en él excepto los controladores de tamaño.  
  
2.  Arrastre la selección a su nueva ubicación.  
  
3.  Para delimitar la selección en la imagen en su nueva ubicación, haga clic fuera del borde de selección.  
  
 Para obtener más información sobre cómo dibujar con una selección, consulte [crear un pincel personalizado](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)


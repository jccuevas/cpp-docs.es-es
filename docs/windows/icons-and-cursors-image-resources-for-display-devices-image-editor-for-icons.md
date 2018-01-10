---
title: "Iconos y cursores: recursos de imagen para dispositivos de presentación (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.icon
dev_langs: C++
helpviewer_keywords:
- cursors [C++], creating
- image resources, display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices, creating icons for
- cursors [C++], hot spots
- icons [C++], types
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99ed2e99c3a08b473dcc786ed47bc088b8fd8a4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons"></a>Iconos y cursores: recursos de imagen para dispositivos de presentación (Editor de imágenes para iconos)
Los iconos y cursores son recursos gráficos que pueden contener varias imágenes de diferentes tamaños y combinaciones de colores para distintos tipos de dispositivos de pantalla. Además, un cursor tiene una "zona activa", la ubicación que Windows usa para realizar un seguimiento de su posición. Tanto los iconos como los cursores se crean y se editan en el editor de imágenes, al igual que los mapas de bits y otras imágenes.  
  
 Al crear un icono o cursor nuevo, el editor de imágenes crea primero una imagen de un tipo estándar. La imagen se rellena inicialmente con el color de la pantalla (transparente). Si la imagen es un cursor, la zona activa es inicialmente la esquina superior izquierda (coordenadas 0,0).  
  
 De forma predeterminada, el editor de imágenes admite la creación de imágenes adicionales para los dispositivos que se muestran en la tabla siguiente. Puede crear imágenes para otros dispositivos escribiendo parámetros de ancho, alto y número de colores en el [cuadro de diálogo Imagen personalizada](custom-image-dialog-box-image-editor-for-icons.md).  
  
> [!NOTE]
>  Con el Editor de imágenes, se pueden ver imágenes de 32 bits, pero no se pueden editar.  
  
|Color|Ancho (píxeles)|Alto (píxeles)|  
|-----------|----------------------|-----------------------|  
|Monocromático|16|16|  
|Monocromático|32|32|  
|Monocromático|48|48|  
|Monocromático|64|64|  
|Monocromático|96|96|  
|16|16|16|  
|16|32|32|  
|16|64|64|  
|16|48|48|  
|16|96|96|  
|256|16|16|  
|256|32|32|  
|256|48|48|  
|256|64|64|  
|256|96|96|  
  
-   [Crear una imagen de dispositivo nueva (icono o cursor)](../windows/creating-a-device-image-image-editor-for-icons.md)  
  
-   [Agregar una imagen para otro dispositivo de presentación](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)  
  
-   [Copiar una imagen de dispositivo](../windows/copying-a-device-image-image-editor-for-icons.md)  
  
-   [Eliminar una imagen de dispositivo](../windows/deleting-a-device-image-image-editor-for-icons.md)  
  
-   [Crear zonas transparentes o inversas en las imágenes de dispositivo](../windows/creating-transparent-or-inverse-regions-in-device-images.md)  
  
-   [Crear un nuevo icono o cursor de 256 colores](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
  
-   [Establecer la zona activa del cursor](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)   
 [Iconos](http://msdn.microsoft.com/library/windows/desktop/ms646973)   
 [Cursores](http://msdn.microsoft.com/library/windows/desktop/ms646970)


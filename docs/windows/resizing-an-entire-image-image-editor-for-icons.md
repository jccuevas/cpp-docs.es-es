---
title: Cambiar el tamaño de una imagen completa (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- size [C++], images
- images [C++], resizing
- resizing images
ms.assetid: 10782937-7eb4-4340-bdec-618ee7d7904b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9104feac603819b9420d315e619182722c87474
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606223"
---
# <a name="resizing-an-entire-image-image-editor-for-icons"></a>Cambiar el tamaño de una imagen completa (Editor de imágenes para iconos)
### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Para cambiar el tamaño de una imagen completa mediante la ventana Propiedades  
  
1.  Abra la imagen cuyas propiedades desea cambiar.  
  
2.  En el **ancho** y **alto** cuadros en el [ventana propiedades](/visualstudio/ide/reference/properties-window), escriba las dimensiones que desee.  
  
     Si va a aumentar el tamaño de la imagen, el editor de imágenes amplía la imagen a la derecha, hacia abajo, o ambos y rellena la nueva región con el color de fondo actual. No se ajusta la imagen.  
  
     Si va a reducir el tamaño de la imagen, el editor de imágenes recorta la imagen a la derecha o el borde inferior o ambos.  
  
    > [!NOTE]
    >  Para cambiar el tamaño de la imagen completa para cambiar el tamaño de una selección parcial no puede usar las propiedades Width y Height.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Cambiar el tamaño de una imagen](../windows/resizing-an-image-image-editor-for-icons.md)
---
title: Paneles de ventana (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a38341f6c6bcbcdec6bb4e6f5e5820fa759e6dab
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652030"
---
# <a name="window-panes-image-editor-for-icons"></a>Paneles de la ventana (Editor de imágenes para iconos)
El **Editor de imágenes** ventana muestra una imagen de normalmente en dos paneles separados por una barra divisora. Una vista es el tamaño real y la otra se amplía (el factor de ampliación predeterminado es 6). Las vistas de estos dos paneles se actualizan automáticamente: los cambios realizados en un panel se muestran inmediatamente en el otro. Los dos paneles facilitan el trabajo en la vista ampliada de la imagen, en el que pueda distinguir los píxeles individuales y, al mismo tiempo, observar el efecto del trabajo en la vista de tamaño real de la imagen.  
  
 Utiliza el espacio se necesita el panel izquierdo (la mitad de la **imagen** ventana) para mostrar la vista de ampliación 1:1 (valor predeterminado) de la imagen. El panel derecho muestra la imagen ampliada (ampliación 6:1 de forma predeterminada). También puede [cambiar la ampliación](../windows/changing-the-magnification-factor-image-editor-for-icons.md) en cada panel con el **Magnify** herramienta en el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o mediante las teclas de aceleración.  
  
 Puede ampliar el panel menor de la **Editor de imágenes** ventana y usar los dos paneles para mostrar diferentes regiones de una imagen grande. Haga clic en el panel para seleccionarlo.  
  
 Puede cambiar el tamaño relativo de los paneles colocando el puntero en la barra de división y al mover la barra de división hacia la izquierda o derecha. Si desea trabajar en un solo panel, puede mover la barra de división a ambos lados.  
  
 Si el **Editor de imágenes** panel es ampliada por un factor de 4 o superior, puede [mostrar una cuadrícula de píxeles](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md) que delimita los píxeles individuales de la imagen.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)
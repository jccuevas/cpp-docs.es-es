---
title: "Paneles de la ventana (Editor de imágenes para iconos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs: C++
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ce9716e810f48c237eabb0ea11b222e3590d795b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="window-panes-image-editor-for-icons"></a>Paneles de la ventana (Editor de imágenes para iconos)
Normalmente, la ventana del Editor de imágenes muestra una imagen en dos paneles separados por una barra divisora. Una vista es el tamaño real y la otra está ampliada (el factor de ampliación predeterminado es 6). Las vistas de estos dos paneles se actualizan automáticamente: los cambios que realice en un panel se muestran inmediatamente en la otra. Los dos paneles facilitan el trabajo en una vista ampliada de la imagen, en el que pueda distinguir píxeles individuales y, al mismo tiempo, observar el efecto del trabajo en la vista de tamaño real de la imagen.  
  
 El panel izquierdo se utiliza como todo el espacio que necesita (hasta la mitad de la ventana de la imagen) para mostrar la vista de ampliación 1:1 (valor predeterminado) de la imagen. El panel derecho muestra la imagen ampliada (ampliación 6:1 de forma predeterminada). También puede [cambiar la ampliación](../windows/changing-the-magnification-factor-image-editor-for-icons.md) en cada panel utilizando el **Magnify** herramienta en el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o mediante las teclas de aceleración.  
  
 Puede ampliar el panel menor de la ventana del Editor de imágenes y usar los dos paneles para mostrar diferentes regiones de una imagen grande. Haga clic en el panel para seleccionarlo.  
  
 Puede cambiar el tamaño relativo de los paneles colocando el puntero en la barra de división y moviendo la barra de división hacia la izquierda o derecha. Si desea trabajar en un solo panel, puede mover la barra de división a ambos lados.  
  
 Si el panel del editor de imágenes se amplía en un factor de 4 o superior, puede [mostrar una cuadrícula de píxeles](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md) que delimita los píxeles individuales de la imagen.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](https://msdn.microsoft.com/library/f45fce5x.aspx) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](https://msdn.microsoft.com/library/xbx3z216.aspx). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)


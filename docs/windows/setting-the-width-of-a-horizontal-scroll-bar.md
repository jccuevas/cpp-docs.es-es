---
title: Establecer el ancho de una barra de desplazamiento Horizontal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls, scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars, displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars, width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54b68ec8f780fc8022543813b412eaff2045cbdf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645609"
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>Establecer el ancho de una barra de desplazamiento horizontal
Cuando se agrega un cuadro de lista con una barra de desplazamiento horizontal para un cuadro de diálogo mediante clases de MFC, la barra de desplazamiento no aparecerá automáticamente en la aplicación.  
  
### <a name="to-make-the-scroll-bar-appear"></a>Para que aparezca la barra de desplazamiento  
  
1.  Establecer un ancho máximo para el elemento más amplio mediante una llamada a [CListBox:: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) en el código.  
  
     Establecer este valor, la barra de desplazamiento no aparecerán, incluso cuando los elementos del cuadro de lista son más amplio que el cuadro.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 MFC  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)
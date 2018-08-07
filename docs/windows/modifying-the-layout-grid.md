---
title: Modificación de la cuadrícula de diseño | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
ms.assetid: ec31f595-7542-485b-806f-efbaeccc1b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9817c1f24490d333f1596292f3b9ea1aa3ba40ae
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606941"
---
# <a name="modifying-the-layout-grid"></a>Modificar la cuadrícula de diseño
Cuando se colocan u organizar controles en un cuadro de diálogo, puede usar la cuadrícula de diseño para una ubicación más precisa. Cuando la cuadrícula está activada, los controles aparecen en "Ajustar a" las líneas de puntos de la cuadrícula como si estuvieran imantados. Puede activar y desactivar la esta característica "Ajustar a la cuadrícula" y cambiar el tamaño de las celdas de cuadrícula de diseño.  
  
### <a name="to-turn-the-layout-grid-on-or-off"></a>Para activar y desactivar la cuadrícula de diseño  
  
1.  Desde el **formato** menú, elija **configuración de la guía**.  
  
2.  En el [cuadro de diálogo de configuración de guía](../windows/guide-settings-dialog-box.md), active o desactive el **cuadrícula** botón.  
  
     Todavía puede controlar la cuadrícula en ventanas del editor de cuadro de diálogo individuales mediante el **Alternar cuadrícula** situado en la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
### <a name="to-change-the-size-of-the-layout-grid"></a>Para cambiar el tamaño de la cuadrícula de diseño  
  
1.  Desde el **formato** menú, elija **configuración de la guía**.  
  
2.  En el [cuadro de diálogo de configuración de guía](../windows/guide-settings-dialog-box.md), escriba el alto y ancho en DLU para las celdas de la cuadrícula. El alto o ancho mínimo es de 4 DLU. Para obtener más información sobre las unidades DLU, vea [la disposición de los controles en cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Estados del Editor de cuadro de diálogo (guías y cuadrículas)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)
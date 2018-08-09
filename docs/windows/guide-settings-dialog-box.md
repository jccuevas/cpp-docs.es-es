---
title: Guía de cuadro de diálogo Configuración | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- Dialog editor, snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 271a56881f2710a7fb7c18dadeb7c36d4d6a3232
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648001"
---
# <a name="guide-settings-dialog-box"></a>Configuración de las guías (Cuadro de diálogo)
## <a name="layout-guides"></a>Guías de diseño  
 Muestra la configuración de las guías de diseño.  
  
### <a name="none"></a>Ninguna  
  
 Oculta las herramientas de diseño.  
  
### <a name="rulers-and-guides"></a>Reglas y guías  
  
 Cuando se habilita, agrega reglas a las herramientas de diseño; las guías se pueden colocar en las reglas. Las guías predeterminadas son los márgenes, que se pueden mover arrastrando. Haga clic en las reglas para ubicar a una guía. Los controles "ajustarán" a las guías cuando se mueven los controles a través o junto a ellos. Los controles también se mueven con una guía de una vez que se conectan a él. Cuando un control está asociado a una guía en cada lado y se mueve una guía, el control cambia de tamaño.  
  
### <a name="grid"></a>Cuadrícula  
  
 Crea una cuadrícula de diseño. Nuevos controles se alinearán automáticamente a la cuadrícula.  
  
## <a name="grid-spacing"></a>espaciado de cuadrícula  
 Muestra la configuración para el espaciado de cuadrícula en unidades de cuadro de diálogo (DLU).  
  
### <a name="width-dlus"></a>Ancho: DLU  
  
 Establece el ancho de la cuadrícula de diseño en DLU. Una DLU horizontal es el ancho promedio de la fuente del cuadro de diálogo dividido por cuatro.  
  
### <a name="height-dlus"></a>Alto: DLU 
  
 Establece el alto de la cuadrícula de diseño en DLU. Una vertical equivale al alto medio de la fuente del cuadro de diálogo dividido por ocho.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Modificación de la cuadrícula de diseño](../windows/modifying-the-layout-grid.md)   
 [Estados del Editor de cuadros de diálogo (guías y cuadrículas)](../windows/dialog-editor-states-guides-and-grids.md)
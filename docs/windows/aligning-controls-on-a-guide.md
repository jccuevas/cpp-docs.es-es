---
title: "Alinear controles en una guía | Documentos de Microsoft"
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
- DLUs (dialog units)
- controls [C++], aligning
- Dialog editor, snap to guides
- guides, tick mark interval
- dialog box controls, placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eed9acf533939d305e42478bb87307bc0a055d3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="aligning-controls-on-a-guide"></a>Alinear controles en una guía
Los controladores de tamaño de los controles de ajustarán a las guías cuando se mueven los controles y las guías se ajustan a los controles (si no hay ningún control ajustado previamente a la guía). Cuando se mueve una guía, se mueven también los controles que se ajustan a él. Controles ajustados a más de una guía cambian de tamaño cuando se mueve una de las guías.  
  
 Las marcas de graduación en las reglas que determinan el espaciado de las guías y los controles se definen mediante unidades de cuadro de diálogo (DLU). Las unidades se basan en el tamaño de la fuente del cuadro de diálogo, normalmente de 8 puntos MS Shell Dlg. Una DLU horizontal equivale al ancho medio de la fuente del cuadro de diálogo dividido por cuatro. Una DLU vertical equivale al alto medio de la fuente dividido por ocho.  
  
### <a name="to-size-a-group-of-controls-with-guides"></a>Para cambiar el tamaño de un grupo de controles con guías  
  
1.  Ajustar un lado del control (o controles) a una guía.  
  
2.  Arrastre a una guía al otro lado del control (o controles).  
  
     Si es necesario con varios controles, cambiar el tamaño de cada uno de ellos para ajustar a la segunda guía.  
  
3.  Mueva una de las guías para cambiar el tamaño del control (o controles).  
  
### <a name="to-change-the-intervals-of-the-tick-marks"></a>Para cambiar los intervalos de las marcas de graduación  
  
1.  Desde el **formato** menú, elija **configuración de la guía**.  
  
2.  En el [cuadro de diálogo de configuración de guía](../windows/guide-settings-dialog-box.md), en la **espaciado de cuadrícula** , a continuación, especifique un nuevo ancho y alto en DLU.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Estados del Editor de cuadro de diálogo (guías y cuadrículas)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)


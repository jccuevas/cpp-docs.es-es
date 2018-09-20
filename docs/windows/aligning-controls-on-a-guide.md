---
title: Alinear controles en una guía | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 648d78466b912f5f1f8c6a83065a07861ab9a7f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374430"
---
# <a name="aligning-controls-on-a-guide"></a>Alinear controles en una guía

Los controladores de tamaño de los controles se ajustan a las guías cuando se mueven los controles y las guías se ajustan a los controles (si no hay ningún control previamente ajustados a la guía). Cuando se mueve una guía, también se mueven los controles que se ajustan a él. Controles ajustados a más de una guía cambian de tamaño cuando se mueve una de las guías.

Las marcas de graduación en las reglas que determinan el espaciado de las guías y los controles se definen mediante unidades de cuadro de diálogo (DLU). Las unidades se basan en el tamaño de la fuente del cuadro de diálogo, normalmente de 8 puntas MS Shell Dlg. Una DLU horizontal es el ancho promedio de la fuente del cuadro de diálogo dividido por cuatro. Una vertical equivale al alto medio de la fuente dividido por ocho.

### <a name="to-size-a-group-of-controls-with-guides"></a>Para cambiar el tamaño de un grupo de controles con guías

1. Ajustar un lado del control (o controles) a una guía.

2. Arrastre a una guía para el otro lado del control (o controles).

   Si es necesario con varios controles, cambiar el tamaño de cada uno que se ajuste a la segunda guía.

3. Mueva una de las guías para cambiar el tamaño del control (o controles).

### <a name="to-change-the-intervals-of-the-tick-marks"></a>Cambiar los intervalos de las marcas de graduación

1. Desde el **formato** menú, elija **configuración de la guía**.

2. En el [cuadro de diálogo de configuración de guía](../windows/guide-settings-dialog-box.md), en el **espaciado de cuadrícula** , especifique un nuevo ancho y alto en DLU.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Estados del Editor de cuadros de diálogo (guías y cuadrículas)](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)
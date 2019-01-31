---
title: Alinear controles
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
ms.openlocfilehash: abfae0f0146fa736a6427eb1180805717ce8a78e
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484986"
---
# <a name="align-controls"></a>Alinear controles

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

Los procedimientos siguientes muestran cómo alinear los controles:

## <a name="to-align-groups-of-controls"></a>Para alinear grupos de controles

1. [Seleccione los controles](../windows/selecting-multiple-controls.md) que desee alinear. Asegúrese de seleccionar el control que desea que el control dominante en primer lugar o establecerlo el control dominante antes de ejecutar la alineación o ajustar el tamaño de comando.

   La posición final del grupo de controles depende de la posición del control principal. Para obtener más información sobre cómo seleccionar el control dominante, vea [especificar el Control dominante](../windows/specifying-the-dominant-control.md).

1. Desde el **formato** menú, elija **alinear**y, a continuación, elija una de las alineaciones siguientes:

   - `Lefts`: alinea los controles seleccionados a lo largo de los lados izquierdos.

   - `Centers`: alinea los controles seleccionados horizontalmente a lo largo de sus puntos centrales.

   - `Rights`: alinea los controles seleccionados a lo largo de los lados derecho.

   - `Tops`: alinea los controles seleccionados por sus bordes superiores.

   - `Middles`: alinea los controles seleccionados verticalmente a lo largo de sus puntos medios.

   - `Bottoms`: alinea los controles seleccionados a lo largo de su borde inferior.

## <a name="to-even-the-spacing-between-controls"></a>Incluso el espaciado entre controles

El **diálogo** editor le permite a los controles del espacio uniformemente entre los controles más externos seleccionados.

1. Seleccione los controles que desee reorganizar.

1. Desde el **formato** menú, elija **espaciar uniformemente**y, a continuación, elija una de las alineaciones siguientes:

   - `Across`: espacio controles uniformemente entre el extremo izquierdo y el extremo derecho control seleccionado.

   - `Down`: espacio controles uniformemente entre el primer y el más bajo control seleccionado.

## <a name="to-center-controls-in-a-dialog-box"></a>Para centrar controles en un cuadro de diálogo

1. Seleccione el control o controles que desea reorganizar.

1. Desde el **formato** menú, elija **centrar en el cuadro de diálogo**y, a continuación, elija una de las distribuciones siguientes:

   - `Vertical`: los controles verticalmente en el cuadro de diálogo del centro.

   - `Horizontal`: Centrar controles horizontalmente en el cuadro de diálogo.

## <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>Organizar botones de comando a la derecha o inferior de un cuadro de diálogo

1. Seleccione uno o varios botones de comando.

1. Desde el **formato** menú, elija **organizar botones**y, a continuación, elija una de las distribuciones siguientes:

   - `Right`: alinea los botones de inserción en el borde derecho del cuadro de diálogo.

   - `Bottom`: alinea los botones de inserción en el borde inferior del cuadro de diálogo.

       Si selecciona un control que no sea un botón de comando, su posición no se ve afectada.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Distribución de los controles en los cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)
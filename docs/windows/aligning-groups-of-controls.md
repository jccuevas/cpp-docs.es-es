---
title: Alinear grupos de controles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], aligning
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c791f2951eb7ac9947d48b563bde624bc3b7979f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393586"
---
# <a name="aligning-groups-of-controls"></a>Alinear grupos de controles

El siguiente procedimiento muestra cómo alinear grupos de controles.

### <a name="to-align-groups-of-controls"></a>Para alinear grupos de controles

1. [Seleccione los controles](../windows/selecting-multiple-controls.md) que desee alinear. Asegúrese de seleccionar el control que desea que el control dominante en primer lugar o establecerlo el control dominante antes de ejecutar la alineación o ajustar el tamaño de comando.

   La posición final del grupo de controles depende de la posición del control principal. Para obtener más información sobre cómo seleccionar el control dominante, vea [especificar el Control dominante](../windows/specifying-the-dominant-control.md).

2. Desde el **formato** menú, elija **alinear**y, a continuación, elija una de las alineaciones siguientes:

   - `Lefts`: alinea los controles seleccionados a lo largo de los lados izquierdos.

   - `Centers`: alinea los controles seleccionados horizontalmente a lo largo de sus puntos centrales.

   - `Rights`: alinea los controles seleccionados a lo largo de los lados derecho.

   - `Tops`: alinea los controles seleccionados por sus bordes superiores.

   - `Middles`: alinea los controles seleccionados verticalmente a lo largo de sus puntos medios.

   - `Bottoms`: alinea los controles seleccionados a lo largo de su borde inferior.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Distribución de los controles en los cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)
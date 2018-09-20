---
title: Ajustar el tamaño de los controles individuales | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9932b14b3d3afaa0afdff90c08ce44bf1f8648dc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373485"
---
# <a name="sizing-individual-controls"></a>Cambiar el tamaño de los controles individuales

Use los controladores de tamaño para cambiar el tamaño de un control. Cuando el puntero se coloca en un controlador de tamaño, cambia la forma para indicar las instrucciones que aparecen en el que se puede cambiar el tamaño del control. Controladores de tamaño activos son sólidos; Si un controlador de tamaño está vacío, el control no puede cambiarse a lo largo de ese eje.

También puede cambiar el tamaño de un control ajustando el control a las guías o los márgenes o moviendo un control ajustado y guía fuera de otra.

### <a name="to-size-a-control"></a>Para cambiar el tamaño de un control

1. Seleccione el control.

2. Arrastre los controladores de tamaño para cambiar el tamaño del control:

   - Controladores de tamaño en la parte superior y cambiar el tamaño horizontal o vertical.

   - Controladores de tamaño en las esquinas cambiar el tamaño horizontal y vertical.

   > [!TIP]
   > Puede cambiar el tamaño la unidad de control de un cuadro de diálogo (DLU) a la vez, mantenga presionada la **MAYÚS** clave y usar el **flecha derecha** y **flecha abajo** claves.

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Para cambiar automáticamente el tamaño de un control para ajustar el texto dentro de él

1. Elija **tamaño al contenido** desde el **formato** menú.

\- o -

- Haga clic en el control y elija **tamaño al contenido** en el menú contextual.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)
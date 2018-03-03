---
title: "Ajustar el tamaño de los controles individuales | Documentos de Microsoft"
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
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b019cd2bbf68a4321bafd6dd960ffbcdba2dddf7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sizing-individual-controls"></a>Cambiar el tamaño de los controles individuales
Use los controladores de tamaño para cambiar el tamaño de un control. Cuando el puntero se sitúa en un controlador de tamaño, cambia de forma para indicar las instrucciones que aparecen en el que el control puede cambiar de tamaño. Controladores de tamaño activos son sólidos; Si un controlador de tamaño está vacío, el control no puede cambiarse a lo largo de ese eje.  
  
 También puede cambiar el tamaño de un control ajustando el control a las guías o márgenes o moviendo un control ajustado y alejándolo de otro.  
  
### <a name="to-size-a-control"></a>Para cambiar el tamaño de un control  
  
1.  Seleccione el control.  
  
2.  Arrastre los controladores de tamaño para cambiar el tamaño del control:  
  
    -   Controladores de tamaño en la parte superior y los lados cambian el tamaño horizontal o vertical.  
  
    -   Controladores de tamaño en las esquinas cambian tamaño horizontal y vertical.  
  
    > [!TIP]
    >  Puede cambiar el tamaño de la unidad de control de un cuadro de diálogo (DLU) cada vez manteniendo presionada la tecla MAYÚS y utilizando las teclas de flecha derecha e izquierda.  
  
### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Para ajustar automáticamente el tamaño de un control para ajustar el texto dentro de él  
  
1.  Elija **tamaño al contenido** desde el **formato** menú.  
  
 \- o -  
  
-   Haga clic en el control y elija **tamaño al contenido** en el menú contextual.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)


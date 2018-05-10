---
title: Cambiar el orden de tabulación de controles | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33e6e9624e7e927860a184361d45f855f3a1e4f6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="changing-the-tab-order-of-controls"></a>Cambiar el orden de tabulación de los controles
El orden de tabulación es el orden en el que la tecla TAB mueve el foco de entrada de un control a la siguiente dentro de un cuadro de diálogo. Normalmente en el orden de tabulación se realiza de izquierda a derecha y de arriba a abajo, en un cuadro de diálogo. Cada control tiene un **Tabstop** propiedad que determina si un control recibe el foco de entrada.  
  
### <a name="to-set-input-focus-for-a-control"></a>Para establecer el foco de entrada para un control  
  
1.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), seleccione **True** o **False** en el **Tabstop** propiedad.  
  
 Incluso los controles que no tienen la propiedad Tabstop establecida en True deberán formar parte del orden de tabulación. Esto puede ser importante, por ejemplo, cuando se [definir teclas de acceso (teclas de acceso)](../windows/defining-mnemonics-access-keys.md) para los controles que no tienen títulos. Texto estático que contiene una clave de acceso asociada a un control debe preceder inmediatamente el control relacionado en el orden de tabulación.  
  
> [!NOTE]
>  Si el cuadro de diálogo contiene controles superpuestos, al cambiar el orden de tabulación puede cambiar la manera en que se muestran los controles. Controles que se incluyen más adelante en el orden de tabulación se muestran siempre encima de todos los controles superpuestos que preceden a ellos en el orden de tabulación.  
  
#### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Para ver el orden de tabulación actual para todos los controles en un cuadro de diálogo  
  
1.  En el **formato** menú, haga clic en **orden de tabulación**.  
  
 \- o -  
  
-   Presione CTRL + D.  
  
#### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Para cambiar el orden de tabulación para todos los controles en un cuadro de diálogo  
  
1.  En el **formato** menú, haga clic en **orden de tabulación**.  
  
     Un número en la esquina superior izquierda de cada control muestra su lugar en el orden de tabulación actual.  
  
2.  Establecer el orden de tabulación haciendo clic en cada control en el orden en que desea que la tecla TAB para seguir.  
  
3.  Presione **ENTRAR** para salir **orden de tabulación** modo.  
  
    > [!TIP]
    >  Una vez que entrar en el modo de orden de tabulación, también puede presionar ESC o ENTRAR se deshabilita la capacidad de cambiar el orden de tabulación.  
  
#### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Para cambiar el orden de tabulación de dos o más controles  
  
1.  Desde el **formato** menú, elija **orden de tabulación**.  
  
2.  Especifique que se iniciará el cambio en el orden. Para ello, mantenga presionada la **CTRL** clave y haga clic en el control anterior a aquél donde desea cambiar el orden para comenzar.  
  
     Por ejemplo, si desea cambiar el orden de los controles 7 al 9, mantenga presionada la tecla CTRL, a continuación, seleccione primero el control 6.  
  
    > [!NOTE]
    >  Para establecer un control determinado en el número 1 (primero en el orden de tabulación), haga doble clic en el control.  
  
3.  Suelte la tecla CTRL y, a continuación, haga clic en los controles en el orden que desee que la tecla TAB para seguir desde ese punto.  
  
4.  Presione **ENTRAR** para salir **orden de tabulación** modo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Organización de los controles de cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)


---
title: Cambiar el orden de tabulación de controles | Microsoft Docs
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
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 822e0c5ac0232ac30e4db63b3605fda0126959de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434601"
---
# <a name="changing-the-tab-order-of-controls"></a>Cambiar el orden de tabulación de los controles

El orden de tabulación es el orden en que el **ficha** tecla mueve el foco de entrada de un control al siguiente en un cuadro de diálogo. Normalmente, el orden de tabulación se realiza de izquierda a derecha y de arriba a abajo en un cuadro de diálogo. Cada control tiene un **Tabstop** propiedad que determina si un control recibe el foco de entrada.

### <a name="to-set-input-focus-for-a-control"></a>Para establecer el foco de entrada para un control

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), seleccione **True** o **False** en el **Tabstop** propiedad.

Incluso los controles que no tienen la **Tabstop** propiedad establecida en **True** deben formar parte del orden de tabulación. Esto puede ser importante, por ejemplo, cuando se [definir teclas de acceso (teclas de acceso)](../windows/defining-mnemonics-access-keys.md) para los controles que no tienen títulos. Texto estático que contiene una clave de acceso para un control relacionado debe preceder inmediatamente al control relacionado en el orden de tabulación.

> [!NOTE]
> Si el cuadro de diálogo contiene controles que se superponen, el orden de tabulación se cambia la manera en que se muestran los controles. Controles que se proporcionan más adelante en el orden de tabulación se muestran siempre encima de los controles que se superponen que preceden a ellos en el orden de tabulación.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Para ver el orden de tabulación para todos los controles en un cuadro de diálogo

1. En el **formato** menú, haga clic en **orden de tabulación**.

\- o -

- Presione **Ctrl**+**d**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Para cambiar el orden de tabulación para todos los controles en un cuadro de diálogo

1. En el **formato** menú, haga clic en **orden de tabulación**.

   Un número en la esquina superior izquierda de cada control muestra su lugar en el orden de tabulación.

2. Establecer el orden de tabulación, haga clic en cada control en el orden que desee la **ficha** clave para seguir.

3. Presione **ENTRAR** para salir **orden de tabulación** modo.

   > [!TIP]
   > Una vez que escriba **orden de tabulación** modo, puede presionar **Esc** o **ENTRAR** para deshabilitar la capacidad de cambiar el orden de tabulación.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Para cambiar el orden de tabulación para dos o más controles

1. Desde el **formato** menú, elija **orden de tabulación**.

2. Especifique donde se iniciará el cambio en el orden. Para ello, mantenga presionada la **Ctrl** clave y haga clic en el control antes de aquél en el que desea cambiar el orden para empezar a.

   Por ejemplo, si desea cambiar el orden de los controles `7` a través de `9`, mantenga presionada la tecla **Ctrl**, a continuación, seleccione el control `6` primero.

   > [!NOTE]
   > Para configurar un control específico en número `1` (primero en el orden de tabulación), haga doble clic en el control.

3. Versión del **Ctrl** clave, a continuación, haga clic en los controles en el orden que desee la **ficha** clave seguir desde ese punto.

4. Presione **ENTRAR** para salir **orden de tabulación** modo.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Distribución de los controles en los cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)
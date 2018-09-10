---
title: Ajustar el tamaño de un Control al agregarlo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: 06b1dd2b-0ba1-4e1f-adc3-cb73679f765e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da998c748a3471f053c922e0a80c33d1526b2055
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313148"
---
# <a name="sizing-a-control-while-you-add-it"></a>Cambiar el tamaño de un control al agregarlo

### <a name="to-size-a-control-while-you-add-it"></a>Cambiar el tamaño de un control al agregarlo

1. Seleccione un control en el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox).

2. Coloque el cursor (que aparece como en cruz) donde desea que la esquina superior izquierda del nuevo control en el cuadro de diálogo.

3. Haga clic y mantenga presionado el botón del mouse para fijar la esquina superior izquierda del control en el cuadro de diálogo, arrastre el cursor a la derecha y hacia abajo hasta que el control es el tamaño que desee.

   > [!NOTE]
   > En realidad puede anclar cualquiera de las cuatro esquinas del control que se está dibujando. Este procedimiento utiliza la esquina superior izquierda como ejemplo.

4. Suelte el botón del mouse. El control se coloca en el cuadro de diálogo en el tamaño especificado.

   > [!TIP]
   > Puede cambiar el tamaño del control después de colocarlo en el cuadro de diálogo, mueva los controladores de tamaño en el borde del control. Para obtener más información, consulte [controles individuales de ajuste de tamaño](../windows/sizing-individual-controls.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)  
[Agregar controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)
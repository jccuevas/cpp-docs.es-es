---
title: Seleccionar controles | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, selecting controls
- dominant controls
- dialog box controls, selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4a8d5260b721bf829c73f587ccd691db5543e40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892779"
---
# <a name="selecting-controls"></a>Seleccionar controles
Seleccione los controles de tamaño, alinear, mover, copiar, o eliminarlas y, a continuación, realizar la operación que desee. En la mayoría de los casos, debe seleccionar más de un control que se utilizarán las herramientas de ajuste de tamaño y alineación en el [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
 Cuando se selecciona un control, tiene un borde sombreado alrededor de ella con sólidos (activos) o huecos (inactivos) "ajustar el tamaño de los identificadores," pequeños cuadros que aparecen en el borde de selección. Cuando se seleccionan varios controles, el control dominante tiene controladores de tamaño sólido; todos los controles seleccionados tienen controladores de tamaño vacío.  
  
 Cuando se cambia el tamaño o alinear varios controles, el editor de cuadro de diálogo utiliza el "control dominante" para determinar cómo los demás controles o un tamaño alineados. De forma predeterminada, el control dominante es el primer control seleccionado.  
  
-   [Selección de varios controles](../windows/selecting-multiple-controls.md)  
  
-   [Especificación del control dominante](../windows/specifying-the-dominant-control.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)


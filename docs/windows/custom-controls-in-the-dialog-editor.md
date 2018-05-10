---
title: Controles personalizados en el Editor de cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- Custom Control
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [Visual Studio], dialog boxes
- custom controls [Visual Studio]
- dialog box controls, custom (user) controls
- Dialog editor, custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2c2bca249958e4d25ab5377540525da34802ac04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="custom-controls-in-the-dialog-editor"></a>Controles personalizados en el Editor de cuadros de diálogo
El editor de cuadro de diálogo permite usar existente "custom" o controles de "usuario" en una plantilla de cuadro de diálogo.  
  
> [!NOTE]
>  Controles personalizados en este sentido no son deben confundirse con los controles ActiveX. Controles ActiveX a veces se denominan controles personalizados OLE. Además, no se deben confundir estos controles con los controles dibujados por el propietario en Windows.  
  
 Esta funcionalidad está diseñada para permitir el uso de otros controles distintos de los proporcionados por Windows. En tiempo de ejecución, el control está asociado a una clase de ventana (no es el mismo que una clase de C++). Una forma más habitual de realizar la misma tarea consiste en instalar un control, como un control estático, en el cuadro de diálogo. A continuación, en tiempo de ejecución, en la [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funcione, quita el control y reemplazarlo con su propio control personalizado.  
  
 Se trata de una técnica anterior. Hoy en día se recomienda en la mayoría de los casos que escribir un control ActiveX o una subclase de un control común de Windows.  
  
 Estos controles personalizados, estará limitado a:  
  
-   Establecer la ubicación en el cuadro de diálogo.  
  
-   Escriba un título.  
  
-   Identifica el nombre de clase de Windows del control (el código de aplicación debe registrar el control con este nombre).  
  
-   Escriba un valor hexadecimal de 32 bits que establece el estilo del control.  
  
-   Establecer el estilo extendido.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)


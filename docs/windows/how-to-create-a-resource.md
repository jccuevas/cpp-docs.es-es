---
title: 'Cómo: crear un recurso | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3a5c8ee47203f24c1995cfde9dda40912f21467
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-create-a-resource"></a>Cómo: Crear un recurso
> [!NOTE]
>  La Vista de recursos no se admite en las ediciones Express.  
  
### <a name="to-create-a-new-resource-in-resource-view"></a>Para crear un recurso nuevo en la Vista de recursos  
  
1.  Con el foco en el archivo .rc en la [Vista de recursos](../windows/resource-view-window.md), haga clic en el menú **Edición** y elija **Agregar recurso** (o haga clic con el botón secundario en el archivo .rc en la Vista de recursos y haga clic en **Agregar recurso** en el menú contextual).  
  
     **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el [cuadro de diálogo Agregar recurso](../windows/add-resource-dialog-box.md), elija el tipo de recurso que desee agregar al proyecto.  
  
### <a name="to-create-a-new-resource-in-solution-explorer"></a>Para crear un recurso nuevo en el Explorador de soluciones  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en la carpeta del proyecto y elija **Agregar**; a continuación, haga clic en **Agregar recurso** en el menú contextual.  
  
     Si el proyecto no tiene aún un archivo .rc, en este paso se creará uno. A continuación puede repetir este paso para agregar tipos de recurso específicos al nuevo archivo .rc.  
  
2.  En el [cuadro de diálogo Agregar recurso](../windows/add-resource-dialog-box.md), elija el tipo de recurso que desee agregar al proyecto.  
  
### <a name="to-create-a-new-resource-in-class-view"></a>Para crear un recurso nuevo en la Vista de clases  
  
1.  En la [Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario en la clase y seleccione **Agregar**; a continuación, haga clic en **Agregar recurso** en el menú contextual.  
  
2.  En el [cuadro de diálogo Agregar recurso](../windows/add-resource-dialog-box.md), elija el tipo de recurso que desee agregar al proyecto.  
  
### <a name="to-create-a-new-resource-from-the-project-menu"></a>Para crear un recurso nuevo desde el menú Proyecto  
  
1.  En el menú **Proyecto** , seleccione **Agregar recurso**.  
  
 Cuando se crea un recurso nuevo, Visual C++ le asigna un nombre único, por ejemplo, IDD_DIALOG1. Puede personalizar este identificador editando las propiedades del recurso en el editor de recursos asociado o en la [ventana Propiedades](/visualstudio/ide/reference/properties-window).  
  
 Los recursos pueden crearse como recursos nuevos predeterminados (sin plantilla) o según el modelo de una [plantilla](../windows/how-to-use-resource-templates.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.*  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)   
 [Agregar recurso (cuadro de diálogo)](../windows/add-resource-dialog-box.md)
---
title: "How to: Create a Resource | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "toolbars [C++], resources"
  - "resource toolbars"
  - "resources [Visual Studio], creating"
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Create a Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La Vista de recursos no se admite en las ediciones Express.  
  
### Para crear un recurso nuevo en la Vista de recursos  
  
1.  Con el foco en el archivo .rc en la [Vista de recursos](../windows/resource-view-window.md), haga clic en el menú **Edición** y elija **Agregar recurso** \(o haga clic con el botón secundario en el archivo .rc en la Vista de recursos y haga clic en **Agregar recurso** en el menú contextual\).  
  
     **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el [cuadro de diálogo Agregar recurso](../Topic/Add%20Resource%20Dialog%20Box.md), elija el tipo de recurso que desee agregar al proyecto.  
  
### Para crear un recurso nuevo en el Explorador de soluciones  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en la carpeta del proyecto y elija **Agregar**; a continuación, haga clic en **Agregar recurso** en el menú contextual.  
  
     Si el proyecto no tiene aún un archivo .rc, en este paso se creará uno. A continuación puede repetir este paso para agregar tipos de recurso específicos al nuevo archivo .rc.  
  
2.  En el [cuadro de diálogo Agregar recurso](../Topic/Add%20Resource%20Dialog%20Box.md), elija el tipo de recurso que desee agregar al proyecto.  
  
### Para crear un recurso nuevo en la Vista de clases  
  
1.  En la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario en la clase y seleccione **Agregar**; a continuación, haga clic en **Agregar recurso** en el menú contextual.  
  
2.  En el [cuadro de diálogo Agregar recurso](../Topic/Add%20Resource%20Dialog%20Box.md), elija el tipo de recurso que desee agregar al proyecto.  
  
### Para crear un recurso nuevo desde el menú Proyecto  
  
1.  En el menú **Proyecto**, seleccione **Agregar recurso**.  
  
 Cuando se crea un recurso nuevo, Visual C\+\+ le asigna un nombre único, por ejemplo, IDD\_DIALOG1. Puede personalizar este identificador editando las propiedades del recurso en el editor de recursos asociado o en la [ventana Propiedades](../Topic/Properties%20Window.md).  
  
 Los recursos pueden crearse como recursos nuevos predeterminados \(sin plantilla\) o según el modelo de una [plantilla](../Topic/How%20to:%20Use%20Resource%20Templates.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*.  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)   
 [Agregar recurso \(Cuadro de diálogo\)](../Topic/Add%20Resource%20Dialog%20Box.md)
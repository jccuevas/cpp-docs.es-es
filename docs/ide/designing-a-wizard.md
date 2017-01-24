---
title: "Dise&#241;ar un asistente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "asistentes personalizados [C++], diseñar para proyectos"
  - "proyectos [C++], asistentes personalizados"
  - "proyectos de Visual C++, asistentes personalizados"
  - "asistentes [C++], personalizadas"
ms.assetid: a7c0be7e-9297-4fed-83e3-5645c896d56b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dise&#241;ar un asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede que necesite crear proyectos con características estándar que difieran de los asistentes para aplicaciones suministrados con Visual C\+\+.  Para tales tareas, puede utilizar la arquitectura de los asistentes de Visual C\+\+, diseñada para ofrecer extensibilidad y personalización de forma sencilla.  Puede crear un asistente mediante el [Asistente personalizado de Visual C\+\+](../ide/creating-a-custom-wizard.md).  Después de crear el asistente, puede configurarlo para que genere los archivos iniciales necesarios para los proyectos.  
  
 Los asistentes de Visual C\+\+ son controles HTML.  Utilizan el motor del asistente de Visual C\+\+, <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI>, que proporciona servicios comunes como <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI.NavigateToCommandHandler%2A>, <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI.OkCancelAlert%2A>, etc.  Además, el asistente utiliza el motor de script, lo que le permite interpretar tanto código VBScript como [JScript .NET](http://msdn.microsoft.com/es-es/c7e636ee-c10f-45b1-85ec-fe2daca30bf5).  
  
 La arquitectura de asistentes le permitirá obtener acceso a los siguientes modelos de objetos directamente desde los asistentes y llamar a sus métodos, propiedades y eventos desde los archivos HTML o JScript.  Para obtener más información, vea los ejemplos en [Los archivos HTML](../ide/html-files.md) y [El archivo JScript](../ide/jscript-file.md).  
  
-   [Modelo de objeto DTE \(Developer Tools Environment, Entorno de herramientas de desarrollador\)](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)  
  
-   [Modelo de código de Visual C\+\+](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b)  
  
-   [Modelo de proyecto de Visual C\+\+](http://msdn.microsoft.com/es-es/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f)  
  
-   [Modelo de asistente de Visual C\+\+](http://msdn.microsoft.com/es-es/159395ac-33c7-47bf-ad42-4e1435ddc758)  
  
 Vea [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md) para obtener una descripción de cada uno de los elementos del proceso de diseño de un asistente.  
  
## Vea también  
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Pasos para diseñar un asistente](../ide/steps-to-designing-a-wizard.md)   
 [Personalizar un asistente](../ide/customizing-your-wizard.md)
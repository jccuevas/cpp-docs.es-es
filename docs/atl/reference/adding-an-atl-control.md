---
title: "Agregar un control ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, agregar controles"
  - "controles [ATL], agregar a proyectos"
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar un control ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Use este asistente para agregar un objeto de interfaz de usuario a un proyecto que sea compatible con el uso de interfaces para todos los contenedores potenciales.  Para admitir el uso de esas interfaces, el proyecto debe haberse creado como aplicación ATL, o como aplicación MFC compatible con ATL.  Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de una aplicación MFC con ATL.  
  
### Para agregar un control ATL a un proyecto  
  
1.  En el **Explorador de soluciones** o en la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario del mouse en el nombre del proyecto al cual desee agregar el objeto simple ATL.  
  
2.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
3.  En el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md), en el panel Plantillas, haga clic en **Control ATL** y después en **Agregar** para mostrar el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md).  
  
 Mediante el **Asistente para controles ATL**, puede crear uno de estos tres tipos de controles:  
  
-   Un control estándar  
  
-   Un control compuesto  
  
-   Un control DHTML  
  
 Asimismo, puede reducir el tamaño del control y quitar las interfaces que no se utilizan en la mayoría de los contenedores seleccionando **Control mínimo** en la página **Opciones** del asistente.  
  
## Vea también  
 [Adding Functionality to the Composite Control](../../atl/adding-functionality-to-the-composite-control.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [ATLFire Sample](http://msdn.microsoft.com/es-es/5b2649f1-f45b-4cfb-9c4b-4d9459c26b09)
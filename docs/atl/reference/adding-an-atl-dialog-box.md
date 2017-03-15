---
title: "Adding an ATL Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, agregar recursos de cuadro de diálogo"
  - "cuadros de diálogo, ATL"
  - "cuadros de diálogo de MFC, cuadros de diálogo ATL"
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Adding an ATL Dialog Box
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para agregar un cuadro de diálogo ATL a un proyecto, éste debe ser un proyecto ATL o bien un proyecto MFC que sea compatible con ATL.  Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de una aplicación MFC con ATL.  
  
 De manera predeterminada, el Asistente para cuadros de diálogo ATL implementa un cuadro de diálogo derivado de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md).  Esta clase incluye compatibilidad para hospedar controles ActiveX y controles de Windows.  Para no sobrecargar la compatibilidad con controles ActiveX, cuando el asistente genere el código, reemplace todas las instancias de `CAxDialogImpl` con [CSimpleDialog](../../atl/reference/csimpledialog-class.md) o [CDialogImpl](../../atl/reference/cdialogimpl-class.md) como clase base.  
  
> [!NOTE]
>  `CSimpleDialog` solo crea cuadros de diálogo modales que admiten únicamente controles comunes de Windows.  `CDialogImpl` crea cuadros de diálogo modales o no modales.  
  
### Para agregar un recurso de cuadro de diálogo ATL a un proyecto  
  
1.  Cree un proyecto ATL mediante el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md).  
  
2.  En la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario del mouse en el nombre del proyecto y después haga clic en **Agregar** en el menú contextual.  Haga clic en **Agregar clase**.  
  
3.  En el panel Plantillas del cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md), haga clic en **Cuadro de diálogo ATL**.  Haga clic en **Abrir** para mostrar el [Asistente para cuadros de diálogo ATL](../../atl/reference/atl-dialog-wizard.md).  
  
 Para obtener más información, vea [Implementar un cuadro de diálogo](../../atl/implementing-a-dialog-box.md).  
  
## Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Clases de ventanas](../../atl/atl-window-classes.md)   
 [Message Maps](../../atl/message-maps-atl.md)
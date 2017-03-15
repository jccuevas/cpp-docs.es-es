---
title: "Agregar un objeto simple ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.classes.adding.atl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, agregar objetos"
  - "ATL, objetos simples"
  - "objetos [ATL]"
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Agregar un objeto simple ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para agregar un objeto de la biblioteca ATL \(Active Template Library\) a un proyecto, éste debe haberse creado como aplicación COM ATL, o como aplicación MFC compatible con ATL.  Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de una aplicación MFC con ATL.  
  
 Se pueden definir interfaces COM para un nuevo objeto ATL al crearlo por primera vez, o agregarlas más tarde mediante el comando [Implementar interfaz](../../ide/implement-interface-wizard.md) del menú contextual de la Vista de clases.  
  
### Para agregar un objeto simple ATL a un proyecto COM ATL  
  
1.  En el **Explorador de soluciones** o en la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario del mouse en el nombre del proyecto al cual desee agregar el objeto simple ATL.  
  
2.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
3.  En el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md) del panel Plantillas, haga clic en **Objeto simple ATL** y, a continuación, en **Abrir** para mostrar el [Asistente para objetos simples ATL](../../atl/reference/atl-simple-object-wizard.md).  
  
4.  Establezca opciones adicionales para el proyecto en la página [Opciones](../../atl/reference/options-atl-simple-object-wizard.md) del Asistente para objetos simples ATL.  
  
5.  Haga clic en **Finalizar** para agregar el objeto al proyecto.  
  
## Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una nueva interfaz a un proyecto ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)   
 [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md)   
 [Agregar un método](../../ide/adding-a-method-visual-cpp.md)   
 [MFC \(clase\)](../../mfc/reference/adding-an-mfc-class.md)   
 [Agregar una clase genérica de C\+\+](../../ide/adding-a-generic-cpp-class.md)
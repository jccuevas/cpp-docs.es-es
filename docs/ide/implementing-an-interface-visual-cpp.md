---
title: "Implementar una interfaz (Visual C++) | Microsoft Docs"
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
  - "interfaces, implementar"
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementar una interfaz (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para implementar una interfaz, debe contar con un proyecto creado como una aplicación COM ATL o bien como una aplicación MFC que sea compatible con ATL.  Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de una aplicación MFC con ATL.  
  
 Una vez creado el proyecto, para implementar una interfaz, primero debe agregar un objeto ATL.  Para obtener una lista de los asistentes que agregan objetos a los proyectos ATL, vea [Agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).  
  
> [!NOTE]
>  El asistente no admite cuadros de diálogo ATL, servicios Web XML que utilicen ATL, objetos de rendimiento ni contadores de rendimiento.  
  
 Cuando [agregue un control ATL](../atl/reference/adding-an-atl-control.md), puede especificar si implementa interfaces predeterminadas, enumeradas en la página [Interfaces](../atl/reference/interfaces-atl-control-wizard.md) del asistente y definidas en atlcom.h.  
  
 Tras agregar el objeto o el control, puede implementar otras interfaces, ubicadas en cualquier biblioteca de tipos disponible, por medio del Asistente para implementar interfaces.  
  
 Si agrega una interfaz nueva, deberá agregarla manualmente al archivo .idl del proyecto.  Para obtener más información, vea [Agregar una nueva interfaz a un proyecto ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).  
  
### Para implementar una interfaz  
  
1.  En la Vista de clases, haga clic con el botón secundario en el nombre de la clase del objeto ATL.  
  
2.  Haga clic en **Agregar** en el menú contextual y, a continuación, haga clic en **Implementar interfaz** para mostrar el [Asistente para implementar interfaces](../ide/implement-interface-wizard.md).  
  
3.  Seleccione las interfaces que desee implementar en las bibliotecas de tipos apropiadas y haga clic en **Finalizar**.  
  
4.  En la Vista de clases, expanda el nodo Bases e interfaces del objeto, para ver la interfaz que ha implementado y, a continuación, expanda el nodo de la interfaz para ver sus propiedades, métodos y eventos disponibles.  
  
    > [!NOTE]
    >  También puede usar el [Examinador de objetos](http://msdn.microsoft.com/es-es/f89acfc5-1152-413d-9f56-3dc16e3f0470) para examinar los miembros de la interfaz.  
  
## Vea también  
 [Crear una interfaz COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Editar una interfaz COM](../ide/editing-a-com-interface.md)
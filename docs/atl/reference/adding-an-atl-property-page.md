---
title: "Agregar una p&#225;gina de propiedades ATL | Microsoft Docs"
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
  - "ATL projects, agregar páginas de propiedades"
  - "controles [ATL], páginas de propiedades"
  - "páginas de propiedades, agregar"
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Agregar una p&#225;gina de propiedades ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para agregar una página de propiedades ATL \(Active Template Library\), debe contar con un proyecto creado como una aplicación ATL o bien como una aplicación MFC que sea compatible con ATL.  Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de una aplicación MFC con ATL.  
  
 Si agrega una página de propiedades a un control, éste debe ser compatible con la interfaz [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md).  De forma predeterminada, esta interfaz se encuentra en la lista de derivación de la clase de control cuando se [crea un control ATL](../../atl/reference/adding-an-atl-control.md) mediante el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md).  
  
> [!NOTE]
>  Si una clase de control no contiene [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) en su lista de derivación, deberá agregarla manualmente.  
  
### Para agregar una página de propiedades ATL a un proyecto  
  
1.  En el **Explorador de soluciones** o en la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario del mouse en el nombre del proyecto al que desee agregar la página de propiedades ATL.  
  
2.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
3.  En el panel Plantillas del cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md), haga clic en **Página de propiedades ATL** y después seleccione **Abrir.** Se ejecuta el [Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md).  
  
 Una vez creada una página de propiedades para un control, debe suministrar la entrada [PROP\_PAGE](../Topic/PROP_PAGE.md) en el mapa de propiedades del control.  
  
## Vea también  
 [Páginas de propiedades](../../atl/atl-com-property-pages.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [Example: Implementing a Property Page](../../atl/example-implementing-a-property-page.md)
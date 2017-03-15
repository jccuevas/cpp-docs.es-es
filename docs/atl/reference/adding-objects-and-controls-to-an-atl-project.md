---
title: "Agregar objetos y controles a un proyecto ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controles ATL"
  - "ATL projects, agregar controles"
  - "ATL projects, agregar objetos"
  - "controles [ATL], agregar a proyectos"
  - "objetos [C++], agregar a proyectos ATL"
  - "asistentes [C++], ATL projects"
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Agregar objetos y controles a un proyecto ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar uno de los asistentes para código ATL con el fin de agregar un objeto o un control a sus proyectos basados en ATL o MFC.  Para cada objeto o control COM que agregue, el asistente generará archivos .cpp y .h, así como un archivo .rgs para compatibilidad con el Registro basado en script.  Visual Studio incluye los siguientes asistentes para código ATL:  
  
||||  
|-|-|-|  
|[Objeto simple ATL](../../atl/reference/atl-simple-object-wizard.md)|[Cuadro de diálogo ATL](../../atl/reference/atl-dialog-wizard.md)|[ATL \(Control\)](../../atl/reference/atl-control-wizard.md)|  
|[Página de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)|[Componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Consumidor OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md)|  
|[Agregar compatibilidad ATL a MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Asistente para componentes ATL COM\+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Proveedor OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|  
  
> [!NOTE]
>  Antes de agregar un objeto ATL al proyecto, revise los detalles y requisitos del objeto en los temas de Ayuda relacionados.  
  
### Para agregar un objeto o un control mediante el Asistente para controles ATL  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el nodo del proyecto y elija **Agregar** en el menú contextual.  Haga clic en **Agregar clase**.  
  
     Aparecerá el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md).  
  
2.  Con la carpeta ATL seleccionada en el panel Categorías, seleccione un objeto para insertar en el panel Plantillas.  Haga clic en **Abrir**.  Aparecerá el asistente para código correspondiente al objeto seleccionado.  
  
    > [!NOTE]
    >  Si desea agregar un objeto ATL a un proyecto MFC, deberá agregar compatibilidad ATL al proyecto existente.  Para hacerlo, siga las instrucciones descritas en [Agregar compatibilidad con ATL a un proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
     Como alternativa, si intenta agregar un objeto ATL al proyecto MFC sin agregar previamente compatibilidad ATL, Visual Studio le pedirá que especifique si desea agregar compatibilidad ATL al proyecto.  Haga clic en **Sí** para agregar compatibilidad ATL al proyecto y abrir el asistente ATL seleccionado.  
  
## Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C\+\+](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md)
---
title: "Editar una interfaz COM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.com.editing.interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces COM, editar"
  - "métodos [C++], agregar a interfaces COM"
  - "propiedades [C++], agregar a interfaces COM"
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Editar una interfaz COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilizando los comandos del menú contextual de la Vista de clases se pueden definir nuevos métodos y propiedades para las interfaces COM en los proyectos de Visual C\+\+.  Igualmente, en el Cuadro de herramientas se pueden definir eventos de controles ActiveX.  
  
 Para las clases de objetos COM basadas en ATL y en MFC, se puede editar la implementación de la clase al mismo tiempo que se edita la interfaz.  
  
> [!NOTE]
>  Para las interfaces definidas fuera del cuadro de diálogo **Agregar clase**, Visual C\+\+ agrega los métodos o las propiedades al archivo .idl y después agrega fragmentos de código auxiliar \(stubs\) a las clases que implementan métodos, incluso aunque las interfaces se hayan agregado manualmente.  
  
 Los tres asistentes siguientes sirven para personalizar las interfaces existentes.  Están disponibles en la Vista de clases.  
  
|Wizard|Tipo de proyecto|  
|------------|----------------------|  
|[Asistente para agregar propiedades](../ide/names-add-property-wizard.md)|Proyectos ATL o MFC compatibles con ATL.  Haga clic con el botón secundario del mouse en la interfaz a la cual desee agregar una propiedad.<br /><br /> Visual C\+\+ detecta el tipo de proyecto y modifica las opciones correspondientes en el Asistente para agregar propiedades:<br /><br /> -   Para interfaces dispinterface en proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), ejecutar el Asistente para agregar propiedades facilita opciones específicas de MFC.<br />-   Para interfaces de controles ActiveX MFC, el Asistente para agregar propiedades facilita una lista de métodos y propiedades estándar que se pueden usar tal como vienen o personalizarse para mayor control.<br />-   Para el resto de interfaces, los asistentes para agregar propiedades proporcionan opciones de utilidad en la mayoría de las ocasiones.|  
|[Asistente para agregar métodos](../ide/add-method-wizard.md)|Proyectos ATL o MFC compatibles con ATL.  Haga clic con el botón secundario del mouse en la interfaz a la cual desee agregar el método.<br /><br /> Visual C\+\+ detecta el tipo de proyecto y modifica las opciones correspondientes en el Asistente para agregar métodos:<br /><br /> -   Para interfaces dispinterface en proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), ejecutar el Asistente para agregar métodos facilita opciones específicas de MFC.<br />-   Para interfaces de controles ActiveX MFC, el Asistente para agregar métodos facilita una lista de métodos y propiedades estándar que se pueden usar tal como vienen o personalizarse para mayor control.<br />-   Para el resto de interfaces, los asistentes **para agregar métodos** proporcionan opciones de utilidad en la mayoría de las ocasiones.|  
  
 Asimismo, se pueden implementar nuevas interfaces en un control COM haciendo clic con el botón secundario del mouse en la clase del control perteneciente al objeto en la Vista de clases y seleccionando [Implementar interfaz](../ide/implement-interface-wizard.md).  
  
## Vea también  
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Tipos de proyecto de Visual C\+\+](../ide/visual-cpp-project-types.md)
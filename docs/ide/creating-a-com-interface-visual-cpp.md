---
title: "Crear una interfaz COM (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.com.creating.interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces COM, crear"
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear una interfaz COM (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ proporciona asistentes y plantillas para crear proyectos que utilizan COM, definiendo interfaces e interfaces dispinterface para sus objetos y clases de automatización OLE.  
  
 Puede utilizar estos asistentes para realizar las siguientes tres tareas comunes:  
  
-   [Agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     Agregue compatibilidad ATL a una aplicación MFC después de crear un proyecto MFC mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) y ejecutando después el asistente de código **Agregar compatibilidad de ATL a MFC**.  Esta compatibilidad sólo se aplica a los objetos COM simples agregados a un ejecutable MFC o un proyecto de DLL.  Dichos objetos ATL pueden tener múltiples interfaces.  
  
-   [Crear un control ActiveX de MFC](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     Abra el [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) para crear un control ActiveX con una interfaz dispinterface y un mapa de eventos definidos en el archivo .idl y en la clase de control, respectivamente.  
  
-   [Agregar un control ATL](../atl/reference/adding-an-atl-control.md)  
  
     Use una combinación del [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) y el [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) para crear un control ActiveX ATL.  
  
     También puede agregar un control ATL a un proyecto MFC al que haya dotado de compatibilidad con ATL, como se describe más arriba.  Asimismo, si selecciona **Control ATL** en el cuadro de diálogo **Agregar clase** y aún no ha agregado compatibilidad con ATL al proyecto MFC, Visual Studio muestra un cuadro de diálogo que confirma la incorporación de la compatibilidad con ATL al proyecto.  
  
     Este asistente genera código fuente IDL y un mapa COM en las clases del proyecto.  
  
 Una vez abierto el proyecto ATL, el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md) permite usar asistentes y plantillas adicionales para agregar interfaces COM al proyecto.  Los siguientes asistentes permiten establecer una o más interfaces para el objeto:  
  
-   [Asistente para componentes ATL COM\+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md)  
  
-   [Asistente para componentes de páginas Active Server ATL](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [Asistente para controles ATL](../atl/reference/atl-control-wizard.md)  
  
 Asimismo, se pueden implementar nuevas interfaces en un control COM haciendo clic con el botón secundario del mouse en la clase del control perteneciente al objeto en la Vista de clases y seleccionando [Implementar interfaz](../ide/implement-interface-wizard.md).  
  
> [!NOTE]
>  Visual Studio no proporciona un asistente para agregar una interfaz a un proyecto.  Se puede agregar una interfaz a un proyecto ATL o [agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) agregando un objeto simple mediante el [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md).  Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo lo siguiente:  
  
```  
interface IMyInterface {  
};  
  
```  
  
 Vea [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [Agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener más información.  
  
 Visual C\+\+ proporciona varias formas de ver y [editar las interfaces COM](../ide/editing-a-com-interface.md) definidas en los proyectos.  [La Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925) muestra iconos de cualquier interfaz o interfaz dispinterface definidas en un archivo .idl de un proyecto C\+\+.  
  
 Para las clases de objetos COM basados en ATL, la Vista de clases lee el mapa COM de la clase ATL y muestra la relación entre la clase ATL y las interfaces que implementa.  
  
 En la Vista de clases y sus menús contextual se puede trabajar con interfaces como sigue:  
  
-   Agregar objetos ATL a una aplicación basada en MFC.  
  
-   Agregar propiedades, métodos y eventos  
  
-   Saltar directamente al código de interfaz de un elemento haciendo doble clic en éste.  
  
## Vea también  
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)
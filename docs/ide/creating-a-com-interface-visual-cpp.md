---
title: Crear una interfaz COM (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.com.creating.interfaces
dev_langs: C++
helpviewer_keywords: COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7b5820686c3e6f01c37cbf527d0e631e5bcc25c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-com-interface-visual-c"></a>Crear una interfaz COM (Visual C++)
Visual C++ proporciona asistentes y plantillas para crear proyectos que utilizan COM, definiendo interfaces e interfaces dispinterface para los objetos COM y las clases de automatización.  
  
 Puede utilizar a estos asistentes para realizar las siguientes tres tareas comunes:  
  
-   [Adición de compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     Agregar compatibilidad con ATL a una aplicación MFC después de crear un proyecto MFC mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) y, a continuación, ejecuta el **agregar compatibilidad de ATL a MFC** Asistente de código. Esta compatibilidad solo se aplica a objetos COM simples añadidos a un ejecutable MFC o un proyecto DLL. Estos objetos ATL pueden tener varias interfaces.  
  
-   [Creación de un control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     Abra la [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md) para crear un control ActiveX con una interfaz dispinterface y un mapa de eventos definidos en el archivo .idl y la clase de control, respectivamente.  
  
-   [Adición de un control ATL](../atl/reference/adding-an-atl-control.md)  
  
     Usar una combinación de la [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) y [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) para crear un control ActiveX de ATL.  
  
     También puede agregar un control ATL a un proyecto MFC a la que ha agregado compatibilidad con ATL, como se describió anteriormente. Además, si selecciona **Control ATL** en el **Agregar clase** cuadro de diálogo y aún no ha agregado compatibilidad con ATL a un proyecto MFC, Visual Studio muestra un cuadro de diálogo Confirmar agregar compatibilidad ATL a su Proyecto MFC.  
  
     Este asistente genera código fuente IDL y un mapa COM en las clases del proyecto.  
  
 Una vez que tiene un proyecto ATL abierta, la [Agregar clase](../ide/add-class-dialog-box.md) cuadro de diálogo ofrece la posibilidad de asistentes adicionales y plantillas para agregar interfaces COM al proyecto. Los siguientes asistentes le permiten establecer una o más interfaces para el objeto:  
  
-   [Asistente para componentes ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md)  
  
-   [Asistente para componentes de páginas Active Server ATL](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [Asistente para controles ATL](../atl/reference/atl-control-wizard.md)  
  
 Además, se pueden implementar nuevas interfaces en un control COM haciendo clic en la clase del objeto control en la vista de clases y haga clic en [Implementar interfaz](../ide/implement-interface-wizard.md).  
  
> [!NOTE]
>  Visual Studio no proporciona un Asistente para agregar una interfaz a un proyecto. Puede agregar una interfaz a un proyecto ATL o a un [agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) mediante la adición de un objeto simple mediante el [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md). Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo:  
  
```  
interface IMyInterface {  
};  
  
```  
  
 Vea [implementando una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener más información.  
  
 Visual C++ proporciona varias maneras para ver y [editar las interfaces COM](../ide/editing-a-com-interface.md) definidas en los proyectos. [Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925) muestra iconos de cualquier interfaz o dispinterface definida en un archivo .idl en el proyecto de C++.  
  
 Para clases de objetos COM basados en ATL, vista de clases lee el mapa COM en la clase ATL para mostrar la relación entre la clase ATL y las interfaces que implementa.  
  
 En la vista de clases y sus menús contextuales, puede trabajar con interfaces como sigue:  
  
-   Agregar objetos ATL a una aplicación basada en MFC.  
  
-   Agregue los métodos, propiedades y eventos.  
  
-   Saltar directamente a código de la interfaz de un elemento haciendo doble clic en el elemento.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)
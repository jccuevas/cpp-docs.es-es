---
title: Agregar controles y objetos a un proyecto ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.controls
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 319d130b9d8f17875aaa8bac15f546401457b963
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Agregar controles y objetos a un proyecto ATL
Puede utilizar uno de los asistentes para código ATL para agregar un objeto o un control a sus proyectos basados en MFC o ATL. Para cada objeto COM o un control se agregue, el asistente genera archivos .h y .cpp, así como un archivo .rgs para compatibilidad con el registro basado en script. Los asistentes de código ATL siguientes están disponibles en Visual Studio:  
  
||||  
|-|-|-|  
|[Objeto Simple ATL](../../atl/reference/atl-simple-object-wizard.md)|[Cuadro de diálogo ATL](../../atl/reference/atl-dialog-wizard.md)|[Controles de ATL](../../atl/reference/atl-control-wizard.md)|  
|[Página de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)|[Componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Consumidor OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md)|  
|[Agregar compatibilidad con ATL a MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Asistente para componentes ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Proveedor OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|  
  
> [!NOTE]
>  Antes de agregar un objeto ATL al proyecto, debe revisar los detalles y requisitos para el objeto en los temas de ayuda relacionados.  
  
### <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Para agregar un objeto o un control mediante el Asistente para controles ATL  
  
1.  En el Explorador de soluciones, haga clic en el nodo del proyecto y haga clic en **agregar** en el menú contextual. Haga clic en **Agregar clase**.  
  
     El [Agregar clase](../../ide/add-class-dialog-box.md) aparece el cuadro de diálogo.  
  
2.  Con la carpeta ATL seleccionada en el panel de categorías, seleccione un objeto que se va a insertar en el panel Plantillas. Haga clic en **abiertos**. Aparece el Asistente de código para el objeto seleccionado.  
  
    > [!NOTE]
    >  Si desea agregar un objeto ATL a un proyecto MFC, debe agregar compatibilidad con ATL al proyecto existente. Puede hacerlo siguiendo las instrucciones de [agregar compatibilidad con ATL a un proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
     Como alternativa, si intenta agregar un objeto ATL a un proyecto MFC sin agregar previamente compatibilidad ATL, Visual Studio le pide que especifique si desea que se agregó al proyecto de compatibilidad ATL. Haga clic en **Sí** para agregar compatibilidad con ATL al proyecto y abrir el asistente ATL seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)


---
title: Editar una interfaz COM | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.com.editing.interfaces
dev_langs: C++
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b8911f23ce8e28f2da13c3d8305f4f13a861bb60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="editing-a-com-interface"></a>Editar una interfaz COM
Mediante el uso de comandos en el menú contextual de vista de clases, puede definir nuevos métodos y propiedades para las interfaces COM en los proyectos de Visual C++. Además, en el cuadro de herramientas, puede definir eventos para controles ActiveX.  
  
 Para las clases de objeto de ATL y MFC basada en COM, puede editar la implementación de la clase al mismo tiempo que se edita la interfaz.  
  
> [!NOTE]
>  Para las interfaces que han definido fuera de la **Agregar clase** cuadro de diálogo, Visual C++ agrega los métodos o propiedades al archivo .idl y que agrega el código auxiliar para las clases que implementan métodos, incluso cuando las interfaces se agregan manualmente.  
  
 Los siguientes tres asistentes ayudarle a personalizar las interfaces existentes. Están disponibles desde la vista de clases:  
  
|Asistente|Tipo de proyecto|  
|------------|------------------|  
|[Asistente para agregar propiedades](../ide/names-add-property-wizard.md)|Proyectos ATL o MFC compatibles con ATL. Haga clic en la interfaz a la que desea agregar la propiedad.<br /><br /> Visual C++ detecta el tipo de proyecto y modifica las opciones en el Asistente para agregar propiedades según corresponda:<br /><br /> -Para interfaces dispinterface en proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), invocar el Asistente para agregar propiedades facilita opciones específicas de MFC.<br />-Para interfaces de controles ActiveX en MFC, el Asistente para agregar propiedades proporciona una lista de métodos y propiedades que puede usar tal como vienen o personalizarse para mayor control estándar.<br />-Para todas las demás interfaces, los asistentes para agregar propiedades proporcionan opciones de utilidad en la mayoría de los casos.|  
|[Asistente para agregar métodos](../ide/add-method-wizard.md)|Proyectos ATL o MFC compatibles con ATL. Haga clic en la interfaz a la que desea agregar el método.<br /><br /> Visual C++ detecta el tipo de proyecto y modifica las opciones en el Asistente para agregar métodos según corresponda:<br /><br /> -Para interfaces dispinterface en proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), invocar el Asistente para agregar métodos facilita opciones específicas de MFC.<br />-Para interfaces de controles ActiveX en MFC, el Asistente para agregar métodos proporciona una lista de métodos y propiedades que puede usar tal como vienen o personalizarse para mayor control estándar.<br />-Para todas las demás interfaces del **Agregar método** asistentes proporcionan opciones de utilidad en la mayoría de los casos.|  
  
 Además, se pueden implementar nuevas interfaces en un control COM haciendo clic en la clase del objeto control en la vista de clases y haga clic en [Implementar interfaz](../ide/implement-interface-wizard.md).  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con archivos de recursos](../windows/working-with-resource-files.md)   
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)
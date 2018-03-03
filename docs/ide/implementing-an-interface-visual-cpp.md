---
title: Implementar una interfaz (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 896ada2c46c68a794265e7344e9b7f7c7f91aebe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-an-interface-visual-c"></a>Implementar una interfaz (Visual C++)
Para implementar una interfaz, debe haber creado un proyecto como una aplicación ATL COM o como una aplicación MFC que sea compatible con ATL. Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o [agregar un objeto ATL a una aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.  
  
 Una vez creado el proyecto, para implementar una interfaz, primero debe agregar un objeto ATL. Vea [agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener una lista de los asistentes que agregan objetos a los proyectos ATL.  
  
> [!NOTE]
>  El asistente no admite cuadros de diálogo ATL, servicios Web XML que utilicen ATL, objetos de rendimiento ni contadores de rendimiento.  
  
 Si se [agregar un control ATL](../atl/reference/adding-an-atl-control.md), puede especificar si desea implementar interfaces predeterminadas, enumeradas en la [Interfaces](../atl/reference/interfaces-atl-control-wizard.md) página del asistente y definidas en atlcom.h.  
  
 Cuando haya agregado el objeto o el control, puede implementar otras interfaces, ubicadas en cualquier biblioteca de tipos disponible mediante el Asistente para implementar interfaces.  
  
 Si va a agregar una nueva interfaz, debe agregarlo manualmente al archivo .idl del proyecto. Vea [agregar una nueva interfaz en un proyecto ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md) para obtener más información.  
  
### <a name="to-implement-an-interface"></a>Para implementar una interfaz  
  
1.  En la vista de clases, haga clic en el nombre de clase para el objeto ATL.  
  
2.  Haga clic en **agregar** desde el menú contextual y, a continuación, haga clic en **Implementar interfaz** para mostrar la [Asistente para implementar interfaces](../ide/implement-interface-wizard.md).  
  
3.  Seleccione las interfaces que desee implementar en las bibliotecas de tipos adecuada y haga clic en **finalizar**.  
  
4.  En la vista de clases, expanda bases de datos del objeto y el nodo de Interfaces para ver la interfaz que ha implementado y, a continuación, expanda el nodo de la interfaz para ver sus propiedades disponibles, métodos y eventos.  
  
    > [!NOTE]
    >  También puede usar el [Examinador de objetos](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) para examinar los miembros de la interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Crear una interfaz COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Editar una interfaz COM](../ide/editing-a-com-interface.md)
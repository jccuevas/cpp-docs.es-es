---
title: Agregar una nueva interfaz en un proyecto ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.interface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 8e4916c60310dd8dcbf0bb9e8c1f151309a32621
ms.lasthandoff: 02/24/2017

---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Agregar una nueva interfaz en un proyecto ATL
Cuando se agrega una interfaz al objeto o control, crear funciones auxiliares para cada método de la interfaz. En el objeto o el control, puede agregar sólo las interfaces que se encuentra actualmente en una biblioteca de tipos existente. Además, debe implementar la clase en la que agregar la interfaz de la [BEGIN_COM_MAP](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333) macro o, si el proyecto admite atributos, debe tener la `coclass` atributo.  
  
 Puede agregar una nueva interfaz al control de dos maneras: manualmente o mediante asistentes para código en la vista de clases.  
  
### <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Utilizar asistentes para código en la vista de clases para agregar una interfaz a un objeto existente o un control  
  
1.  En [la vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre de clase de un control. Por ejemplo, un control total o un control compuesto o cualquier otra clase de control que implemente una macro BEGIN_COM_MAP en su archivo de encabezado.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Implementar interfaz**.  
  
3.  Seleccione las interfaces para implementar en el [Asistente para implementar interfaces](../../ide/implement-interface-wizard.md). Si la interfaz no existe en cualquier biblioteca de tipos disponible, a continuación, debe agregarlo manualmente al archivo .idl.  
  
### <a name="to-add-a-new-interface-manually"></a>Para agregar una nueva interfaz manualmente  
  
1.  Agregue la definición de la nueva interfaz al archivo .idl.  
  
2.  Derive el objeto o el control de la interfaz.  
  
3.  Crear un nuevo [COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/c5363b8b-a1a2-471e-ad3a-d472f6c356c5) para la interfaz o, si el proyecto admite atributos, agregue el `coclass` atributo.  
  
4.  Implementar los métodos en la interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Configuraciones predeterminadas de proyecto ATL](../../atl/reference/default-atl-project-configurations.md)



---
title: Agregar una nueva interfaz en un proyecto ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2c9d0ef4c14760d596a4aa26fa2a929da26c67b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356750"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Agregar una nueva interfaz en un proyecto ATL
Cuando se agrega una interfaz para el objeto o un control, cree funciones auxiliares para cada método en esa interfaz. En el objeto o el control, puede agregar únicamente las interfaces que se encuentra actualmente en una biblioteca de tipos existente. Además, la clase en la que agregar la interfaz debe implementar la [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) macro o, si el proyecto tiene como atributo, debe tener la `coclass` atributo.  
  
 Puede agregar una nueva interfaz para el control de una de dos maneras: manualmente o mediante los asistentes de código de la vista de clases.  
  
### <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Para utilizar los asistentes para código en la vista de clases para agregar una interfaz a un objeto existente o control  
  
1.  En [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre de clase de un control. Por ejemplo, un control total o control compuesto o cualquier otra clase de control que implemente una macro BEGIN_COM_MAP en su archivo de encabezado.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Implementar interfaz**.  
  
3.  Seleccione las interfaces que se va a implementar en el [Asistente para implementar interfaces](../../ide/implement-interface-wizard.md). Si la interfaz no existe en cualquier biblioteca de tipos disponible, a continuación, que debe agregarla manualmente al archivo .idl.  
  
### <a name="to-add-a-new-interface-manually"></a>Para agregar una nueva interfaz manualmente  
  
1.  Agregue la definición de la nueva interfaz al archivo .idl.  
  
2.  Derive el objeto o el control de la interfaz.  
  
3.  Crear un nuevo [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) para la interfaz o, si el proyecto tiene como atributos, agregue el `coclass` atributo.  
  
4.  Implementar los métodos en la interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)


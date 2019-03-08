---
title: Agregar una nueva interfaz en un proyecto ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 29b8fc3caf2d769fcc60772be7fdf1c25f13d100
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285391"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Agregar una nueva interfaz en un proyecto ATL

Cuando se agrega una interfaz para el objeto o el control, crear funciones auxiliares para cada método en esa interfaz. En el objeto o el control, puede agregar sólo las interfaces que se encuentra actualmente en una biblioteca de tipos existente. Además, debe implementar la clase que se agregue la interfaz de la [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) macro o, si se atribuye el proyecto, debe tener el `coclass` atributo.

Puede agregar una nueva interfaz al control de dos maneras: manualmente o mediante los asistentes para código en la vista de clases.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Para usar a los asistentes para código en la vista de clases para agregar una interfaz a un objeto existente o un control

1. En [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en el nombre de clase de un control. Por ejemplo, un control total o un control compuesto o cualquier otra clase de control que implementa una macro BEGIN_COM_MAP en su archivo de encabezado.

1. En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Implementar interfaz**.

1. Seleccione las interfaces que se va a implementar en el [Asistente para implementar interfaces](../../ide/implement-interface-wizard.md). Si la interfaz no existe en cualquier biblioteca de tipos disponible, a continuación, debe agregarlo manualmente al archivo .idl.

## <a name="to-add-a-new-interface-manually"></a>Para agregar una nueva interfaz manualmente

1. Agregue la definición de la interfaz de nuevo al archivo .idl.

1. Derive el objeto o el control de la interfaz.

1. Cree un nuevo [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) para la interfaz o, si se atribuye el proyecto, agregue el `coclass` atributo.

1. Implementar los métodos en la interfaz.

## <a name="see-also"></a>Vea también

[Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

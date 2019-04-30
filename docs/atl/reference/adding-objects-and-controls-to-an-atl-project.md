---
title: Adición de objetos y controles a un proyecto ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: 94478f01655ff68b6b8067771eb3fdab42d1af01
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249091"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Adición de objetos y controles a un proyecto ATL

Puede usar uno de los asistentes de código ATL para agregar un objeto o un control a los proyectos basados en MFC o ATL. Para cada objeto COM o un control Agregar, el asistente genera archivos .h y .cpp, así como un archivo .rgs para compatibilidad con el registro basado en script. Los asistentes de código ATL siguientes están disponibles en Visual Studio:

||||
|-|-|-|
|[Objeto simple ATL](../../atl/reference/atl-simple-object-wizard.md)|[Cuadro de diálogo ATL](../../atl/reference/atl-dialog-wizard.md)|[Control ATL](../../atl/reference/atl-control-wizard.md)|
|[Página de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)|[Componente de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Consumidor OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[Agregar compatibilidad con ATL a MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Asistente para componentes ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Proveedor OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> Antes de agregar un objeto ATL al proyecto, debe revisar los detalles y requisitos para el objeto en los temas de ayuda relacionados.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Para agregar un objeto o un control mediante el Asistente para controles ATL

1. En **el Explorador de soluciones**, haga clic en el nodo del proyecto y haga clic en **agregar** en el menú contextual. Haga clic en **Agregar clase**.

   El [Agregar clase](../../ide/add-class-dialog-box.md) aparece el cuadro de diálogo.

1. Con el **ATL** carpeta seleccionada en el **categorías** panel, seleccione un objeto que se va a insertar en el **plantillas** panel. Haga clic en **Abrir**. Aparece el Asistente de código para el objeto seleccionado.

   > [!NOTE]
   > Si desea agregar un objeto ATL a un proyecto MFC, debe agregar compatibilidad con ATL al proyecto existente. Puede hacerlo siguiendo las instrucciones de [agregar compatibilidad con ATL a un proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Como alternativa, si se intenta agregar un objeto ATL a un proyecto MFC sin agregar previamente compatibilidad con ATL, Visual Studio le pedirá que especifique si desea que la compatibilidad agregada a su proyecto. Haga clic en **Sí** para agregar compatibilidad con ATL al proyecto y abrir el asistente ATL seleccionado.

## <a name="see-also"></a>Vea también

[Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Tipos de proyecto de Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

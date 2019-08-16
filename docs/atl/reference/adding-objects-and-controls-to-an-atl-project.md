---
title: Adición de objetos y controles a un proyecto ATL
ms.date: 05/09/2019
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
ms.openlocfilehash: deaac8f2d6aac02d0cd751e6abebb3b67051200f
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706848"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Adición de objetos y controles a un proyecto ATL

> [!NOTE] 
> El Asistente para componentes COM+ 1.0 ATL, el Asistente para consumidores OLE DB ATL y el Asistente para componentes de páginas Active Server ATL no están disponibles en Visual Studio 2019 ni en versiones posteriores.

Puede usar uno de los asistentes de código ATL para agregar un objeto o un control a los proyectos basados en MFC o ATL. Para cada objeto o control COM que se agregue, el asistente genera archivos .h y .cpp, así como un archivo .rgs para la compatibilidad con el registro basado en scripts. Los asistentes de código ATL siguientes están disponibles en Visual Studio:

||||
|-|-|-|
|[Objeto simple ATL](../../atl/reference/atl-simple-object-wizard.md)|[Cuadro de diálogo ATL](../../atl/reference/atl-dialog-wizard.md)|[Control ATL](../../atl/reference/atl-control-wizard.md)|
|[Página de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)|[Componente de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[Agregar compatibilidad de ATL a MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Asistente para componentes ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Asistente para proveedores OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> Antes de agregar un objeto ATL al proyecto, debe revisar los detalles y requisitos para el objeto en los temas de ayuda relacionados.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Para agregar un objeto o un control mediante el Asistente para controles ATL

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y haga clic en **Agregar** en el menú contextual. Haga clic en **Agregar clase**.

   Aparecerá el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md).

1. Con la carpeta **ATL** seleccionada en el panel **Categorías**, seleccione un objeto para insertar en el panel **Plantillas**. Haga clic en **Abrir**. Aparecerá el asistente de código para el objeto seleccionado.

   > [!NOTE]
   > Si quiere agregar un objeto ATL a un proyecto MFC, tendrá que agregar compatibilidad con ATL al proyecto existente. Para hacerlo, siga las instrucciones de [Adición de compatibilidad con ATL al proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Como alternativa, si intenta agregar un objeto ATL a un proyecto MFC sin agregar previamente compatibilidad con ATL, Visual Studio le pedirá que especifique si quiere que se agregue la compatibilidad al proyecto. Haga clic en **Sí** para agregar compatibilidad con ATL al proyecto y abrir el asistente ATL seleccionado.

## <a name="see-also"></a>Vea también

[Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Tipos de proyectos de C++ en Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

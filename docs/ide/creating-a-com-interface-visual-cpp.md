---
title: Crear una interfaz COM
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.com.creating.interfaces
- vc.codewiz.com.editing.interfaces
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: dfc4b09f4fa42b179bdef91877e0a004caa69187
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693706"
---
# <a name="create-a-com-interface"></a>Crear una interfaz COM

Visual C++ proporciona asistentes y plantillas para crear proyectos que usan interfaces e interfaces dispinterface que definen COM para los objetos y las clases de automatización de COM.

Estos asistentes se pueden usar para realizar las tres tareas habituales siguientes:

- [Agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

  Agregue compatibilidad de ATL a una aplicación MFC después de crear un proyecto MFC mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) y ejecutar el asistente de código **Agregar compatibilidad de ATL a MFC**. Esta compatibilidad solo se aplica a los objetos COM simples que se agregan a un archivo ejecutable de MFC o un proyecto de DLL. Estos objetos ATL pueden tener más de una interfaz.

- [Crear un control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md).

  Abra el [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) para crear un control ActiveX con una interfaz dispinterface y un mapa de eventos definido en el archivo .idl y la clase de control, respectivamente.

- [Agregar un control ATL](../atl/reference/adding-an-atl-control.md).

  Use una combinación del [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) y el [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) para crear un control ActiveX ATL.

  También se puede agregar un control ATL a un proyecto MFC al que se haya agregado compatibilidad de ATL, como se ha explicado arriba. Además, si selecciona **Control ATL** en el cuadro de diálogo **Agregar clase** y todavía no ha agregado compatibilidad de ATL al proyecto MFC, Visual Studio muestra un cuadro de diálogo que confirma la adición de compatibilidad de ATL al proyecto MFC.

  Este asistente genera código fuente de IDL y un mapa COM en las clases del proyecto.

Cuando hay un proyecto ATL abierto, en el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md) se ofrecen asistentes y plantillas adicionales para agregar interfaces COM al proyecto. Los asistentes siguientes permiten establecer una o más interfaces para el objeto:

- [Asistente para componentes COM+ 1.0 ATL](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md)
- [Asistente para componentes de páginas Active Server ATL](../atl/reference/atl-active-server-page-component-wizard.md)
- [Asistente para controles ATL](../atl/reference/atl-control-wizard.md)

Además, puede implementar nuevas interfaces en el control COM. Solo tiene que hacer clic con el botón derecho en la clase de control del objeto en la Vista de clases y elegir [Implementar interfaz](../ide/implement-interface-wizard.md).

> [!NOTE]
> Visual Studio no proporciona ningún asistente para agregar una interfaz a un proyecto. Puede agregar una interfaz a un proyecto ATL o [Agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) si incorpora un objeto simple con el [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md). Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo lo siguiente:

```
interface IMyInterface {
};
```

Para obtener más información, vea [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [Agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ proporciona varias maneras para ver y [editar las interfaces COM](#edit-a-com-interface) definidas en los proyectos. En la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code) se muestran los iconos de cualquier interfaz o interfaz dispinterface definida en un archivo .idl del proyecto de C++.

Para las clases de objetos COM basadas en ATL, la Vista de clases lee el mapa COM en la clase ATL para mostrar la relación entre la clase ATL y las interfaces que implementa.

En la Vista de clases y sus menús contextuales, se puede trabajar con las interfaces de esta forma:

- Agregar objetos ATL a una aplicación basada en MFC.
- Agregar métodos, propiedades y eventos.
- Ir directamente al código de la interfaz de un elemento haciendo doble clic en el elemento.

## <a name="in-this-section"></a>En esta sección

- [Editar una interfaz COM](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>Editar una interfaz COM

Mediante los comandos del menú contextual Vista de clases, se pueden definir métodos y propiedades nuevos para las interfaces COM en los proyectos de Visual C++. Desde el cuadro de herramientas, también se pueden definir eventos para controles ActiveX.

Para las clases de objeto COM basadas en ATL y MFC, se puede editar la implementación de la clase al mismo tiempo que se edita la interfaz.

> [!NOTE]
> En el caso de las interfaces definidas fuera del cuadro de diálogo **Agregar clase**, Visual C++ agrega los métodos o propiedades al archivo .idl y agrega stubs a las clases que implementan métodos, aun cuando las interfaces se agreguen de forma manual.

Los tres asistentes siguientes ayudan a personalizar las interfaces existentes. Están disponibles en la Vista de clases:

|Asistente|Tipo de proyecto|
|------------|------------------|
|[Asistente para agregar propiedades](../ide/names-add-property-wizard.md)|Proyectos de ATL o MFC compatibles con ATL. Haga clic con el botón derecho en la interfaz a la que quiera agregar la propiedad.<br /><br />Visual C++ detecta el tipo de proyecto y modifica las opciones en el Asistente para agregar propiedades según sea necesario:<br /><br />- En el caso de las interfaces dispinterface de proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), la invocación del Asistente para agregar propiedades proporciona opciones específicas para MFC.<br />- Para las interfaces de controles ActiveX MFC, el Asistente para agregar propiedades proporciona una lista de métodos y propiedades estándar que se pueden usar tal cual o personalizar para controlarlos.<br />- Para todas las demás interfaces, los asistentes para agregar propiedades proporcionan opciones de utilidad en la mayoría de los casos.|
|[Asistente para agregar métodos](../ide/add-method-wizard.md)|Proyectos de ATL o MFC compatibles con ATL. Haga clic con el botón derecho en la interfaz a la que quiera agregar el método.<br /><br />Visual C++ detecta el tipo de proyecto y modifica las opciones en el Asistente para agregar métodos según sea necesario:<br /><br />- En el caso de las interfaces dispinterface de proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), la invocación del Asistente para agregar métodos proporciona opciones específicas para MFC.<br />- Para las interfaces de controles ActiveX MFC, el Asistente para agregar métodos proporciona una lista de métodos y propiedades estándar que se pueden usar tal cual o personalizar para controlarlos.<br />- Para todas las demás interfaces, los asistentes para **agregar métodos** proporcionan opciones de utilidad en la mayoría de los casos.|

Además, puede implementar nuevas interfaces en el control COM. Solo tiene que hacer clic con el botón derecho en la clase de control del objeto en la Vista de clases y elegir [Implementar interfaz](../ide/implement-interface-wizard.md).

---
title: Agregar una clase
ms.date: 05/14/2019
f1_keywords:
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: fa53c2af5cd3e81c2d4877ef255430eac9525aad
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182685"
---
# <a name="add-a-class"></a>Agregar una clase

Para agregar una clase en un proyecto de C++, en el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto, elija **Agregar** y luego **Clase**. Se abre el cuadro de diálogo [Agregar clase](#add-class-dialog-box).

Cuando se agrega una clase, se debe especificar un nombre que sea distinto al de las clases que ya existen en MFC o ATL. Si se especifica un nombre que ya existe en alguna de esas bibliotecas, el IDE muestra un mensaje de error.

Si la convención de nomenclatura del proyecto requiere usar un nombre existente, solo se pueden cambiar las mayúsculas y minúsculas de una o varias letras en el nombre porque C++ distingue mayúsculas de minúsculas. Por ejemplo, aunque una clase no se puede denominar `CDocument`, se puede denominar `cdocument`.

## <a name="in-this-section"></a>En esta sección

- [¿Qué tipo de clase quiere agregar?](#what-kind-of-class-do-you-want-to-add)
- [Agregar clase (cuadro de diálogo)](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>¿Qué tipo de clase quiere agregar?

En el cuadro de diálogo **Agregar clase**, cuando se expande el nodo **Visual C++** en el panel de la izquierda, se muestran varias agrupaciones de plantillas instaladas. Los grupos incluyen **CLR**, **ATL**, **MFC** y **C++** . Cuando se selecciona un grupo, en el panel central se muestra una lista de las plantillas disponibles en ese grupo. Cada plantilla contiene los archivos y el código fuente que son necesarios para una clase.

Para generar una clase nueva, seleccione una plantilla en el panel central, escriba un nombre para la clase en el cuadro **Nombre** y seleccione **Agregar**. Se abrirá el **Asistente para agregar clases** para que pueda especificar opciones para la clase.

- Para obtener más información sobre cómo crear clases de MFC, vea [Clases de MFC](../mfc/reference/adding-an-mfc-class.md).

- Para obtener más información sobre cómo crear clases de ATL, vea [Objeto simple ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
> La plantilla **Agregar compatibilidad de ATL a MFC** no crea una clase, pero en su lugar, configura el proyecto para usar ATL. Para obtener más información, vea [Compatibilidad de ATL en un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Para hacer que una clase de C++ que no usa MFC, ATL ni CLR, use la plantilla **Clase de C++** del grupo de plantillas instaladas **C++** . Para obtener más información, vea [Agregar una clase genérica de C++](../ide/adding-a-generic-cpp-class.md).

Existen dos tipos de clases de C++ basadas en formularios. El primero, [CFormView (clase)](../mfc/reference/cformview-class.md), crea una clase de MFC. El segundo crea una clase de Windows Forms de CLR.

## <a name="add-class-dialog-box"></a>Agregar clase (cuadro de diálogo)

El cuadro de diálogo **Agregar clase** contiene plantillas que permiten:

- Abrir a un asistente para código correspondiente, si está disponible. Para obtener más información, vea [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).

   \- o -

- Crear automáticamente una nueva clase propia agregando el código fuente y los archivos adecuados al proyecto.

Puede acceder al cuadro de diálogo **Agregar clase** desde el menú **Proyecto** , el **Explorador de soluciones**o la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Cuando intente agregar una clase que no es adecuada para el proyecto actual, recibirá un mensaje de error. Seleccione **Aceptar** para volver al cuadro de diálogo **Agregar clase**.

### <a name="add-class-templates"></a>Plantillas de Agregar clase

Hay cuatro categorías de plantillas de **Agregar clase** : .NET, ATL, MFC y genérica. Al seleccionar una plantilla en el panel **Plantillas** , el texto que describe la selección aparecerá debajo de los paneles **Categorías** y **Plantillas** .

#### <a name="net"></a>.NET

|Plantilla|Asistente|
|--------------|------------|
|Servicio Web ASP.NET|No disponible|
|Clase de componente (.NET)|No disponible|
|Clase de instalador (.NET)|No disponible|
|Control de usuario (.NET)|No disponible|
|Windows Form (.NET)|No disponible|

#### <a name="atl"></a>ATL

|Plantilla|Asistente|
|--------------|------------|
|Agregar compatibilidad de ATL a MFC|No disponible|
|Control ATL|[Asistente para controles ATL](../atl/reference/atl-control-wizard.md)|
|Cuadro de diálogo ATL|[Asistente para cuadros de diálogo ATL](../atl/reference/atl-dialog-wizard.md)|
|Objeto simple ATL|[Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md)|
|Proveedor de eventos WMI|Asistente para el proveedor de eventos WMI|
|Proveedor de instancias WMI|Asistente para el proveedor de instancias WMI|

#### <a name="mfc"></a>MFC

|Plantilla|Asistente|
|--------------|------------|
|MFC (clase)|[Asistente para agregar clases MFC](../mfc/reference/mfc-add-class-wizard.md)|

#### <a name="generic-classes"></a>Clases genéricas

|Plantilla|Asistente|
|--------------|------------|
|Clase genérica de C++|[Asistente de clases genéricas de C++](../ide/generic-cpp-class-wizard.md)|

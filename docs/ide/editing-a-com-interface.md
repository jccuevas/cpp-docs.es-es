---
title: Editar una interfaz COM
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.com.editing.interfaces
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
ms.openlocfilehash: 338782cbf7cc302c285e8e778389ae28e20f2b14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657371"
---
# <a name="editing-a-com-interface"></a>Editar una interfaz COM

Mediante los comandos del menú contextual Vista de clases, se pueden definir métodos y propiedades nuevos para las interfaces COM en los proyectos de Visual C++. Además, desde el cuadro de herramientas, se pueden definir eventos para los controles ActiveX.

Para las clases de objeto COM basadas en ATL y MFC, se puede editar la implementación de la clase al mismo tiempo que se edita la interfaz.

> [!NOTE]
>  Para las interfaces que se han definido fuera del cuadro de diálogo **Agregar clase**, Visual C++ agrega los métodos o propiedades al archivo .idl, y agrega códigos auxiliares a las clases que implementan los métodos, incluso cuando las interfaces se agregan de forma manual.

Los tres asistentes siguientes ayudan a personalizar las interfaces existentes. Están disponibles desde la Vista de clases:

|Asistente|Tipo de proyecto|
|------------|------------------|
|[Asistente para agregar propiedades](../ide/names-add-property-wizard.md)|Proyectos de ATL o MFC compatibles con ATL. Haga clic con el botón derecho en la interfaz a la que quiera agregar la propiedad.<br /><br />Visual C++ detecta el tipo de proyecto y modifica las opciones en el Asistente para agregar propiedades según corresponda:<br /><br />- Para las interfaces dispinterface de proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), la invocación del Asistente para agregar propiedades proporciona opciones específicas para MFC.<br />- Para las interfaces de controles ActiveX MFC, el Asistente para agregar propiedades proporciona una lista de métodos y propiedades estándar que se pueden usar tal cual o personalizar para controlarlos.<br />- Para todas las demás interfaces, los asistentes para agregar propiedades proporcionan opciones de utilidad en la mayoría de los casos.|
|[Asistente para agregar métodos](../ide/add-method-wizard.md)|Proyectos de ATL o MFC compatibles con ATL. Haga clic con el botón derecho en la interfaz a la que quiera agregar el método.<br /><br />Visual C++ detecta el tipo de proyecto y modifica las opciones en el Asistente para agregar métodos según corresponda:<br /><br />- Para las interfaces dispinterface de proyectos creados mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md), la invocación del Asistente para agregar métodos proporciona opciones específicas para MFC.<br />- Para las interfaces de controles ActiveX MFC, el Asistente para agregar métodos proporciona una lista de métodos y propiedades estándar que se pueden usar tal cual o personalizar para controlarlos.<br />- Para todas las demás interfaces, los asistentes para **agregar métodos** proporcionan opciones de utilidad en la mayoría de los casos.|

Además, se pueden implementar interfaces nuevas en el control COM haciendo clic con el botón derecho en la clase de control del objeto en la Vista de clases y haciendo clic en [Implementar interfaz](../ide/implement-interface-wizard.md).

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br>
[Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)
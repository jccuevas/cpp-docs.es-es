---
title: Crear una interfaz COM (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.creating.interfaces
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e573e65e1b9f3638aaa2f1b25c36d6c959f194d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390105"
---
# <a name="creating-a-com-interface-visual-c"></a>Crear una interfaz COM (Visual C++)

Visual C++ proporciona asistentes y plantillas para crear proyectos que usan interfaces e interfaces dispinterface que definen COM para los objetos y las clases de automatización de COM.

Estos asistentes se pueden usar para realizar las tres tareas comunes siguientes:

- [Adición de compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

   Agregar compatibilidad con ATL a una aplicación MFC después de crear un proyecto MFC mediante el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) y, después, ejecutar el asistente de código **Agregar compatibilidad de ATL a MFC**. Esta compatibilidad solo se aplica a los objetos COM simples que se agregan a un archivo ejecutable de MFC o un proyecto de DLL. Estos objetos ATL pueden tener varias interfaces.

- [Creación de un control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)

   Abra el [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) para crear un control ActiveX con una interfaz dispinterface y un mapa de eventos definidos en el archivo .idl y la clase de control, respectivamente.

- [Adición de un control ATL](../atl/reference/adding-an-atl-control.md)

   Use una combinación del [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) y el [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) para crear un control ActiveX de ATL.

   También se puede agregar un control ATL a un proyecto MFC al que se haya agregado compatibilidad con ATL, como se describió anteriormente. Además, si selecciona **Control ATL** en el cuadro de diálogo **Agregar clase** y todavía no ha agregado compatibilidad con ATL al proyecto MFC, Visual Studio muestra un cuadro de diálogo en el que se confirma que se agrega compatibilidad con ATL al proyecto MFC.

   Este asistente genera código fuente de IDL y un mapa COM en las clases del proyecto.

Una vez abierto el proyecto ATL, en el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md) se ofrecen asistentes y plantillas adicionales para agregar interfaces COM al proyecto. Los asistentes siguientes permiten establecer una o más interfaces para el objeto:

- [Asistente para componentes ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)

- [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md)

- [Asistente para componentes de páginas Active Server ATL](../atl/reference/atl-active-server-page-component-wizard.md)

- [Asistente para controles ATL](../atl/reference/atl-control-wizard.md)

Además, se pueden implementar interfaces nuevas en el control COM haciendo clic con el botón derecho en la clase de control del objeto en la Vista de clases y haciendo clic en [Implementar interfaz](../ide/implement-interface-wizard.md).

> [!NOTE]
>  Visual Studio no proporciona un asistente para agregar una interfaz a un proyecto. Puede agregar una interfaz a un proyecto ATL o a [Agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) mediante la adición de un objeto simple con el [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md). Como alternativa, abra el archivo .idl del proyecto y cree la interfaz escribiendo lo siguiente:

```
interface IMyInterface {
};

```

Vea [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md) y [Agregar controles y objetos a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener más información.

Visual C++ proporciona varias maneras para ver y [editar las interfaces COM](../ide/editing-a-com-interface.md) definidas en los proyectos. En la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code) se muestran los iconos de cualquier interfaz o interfaz dispinterface definida en un archivo .idl del proyecto de C++.

Para las clases de objetos COM basadas en ATL, la Vista de clases lee el mapa COM en la clase ATL para mostrar la relación entre la clase ATL y las interfaces que implementa.

En la Vista de clases y sus menús contextuales, se puede trabajar con las interfaces de esta forma:

- Agregar objetos ATL a una aplicación basada en MFC.

- Agregar métodos, propiedades y eventos.

- Ir directamente al código de la interfaz de un elemento haciendo doble clic en el elemento.

## <a name="see-also"></a>Vea también

[Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)
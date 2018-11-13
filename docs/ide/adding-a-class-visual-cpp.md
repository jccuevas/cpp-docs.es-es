---
title: Agregar una clase (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: 8cdc8dcc4241acb805255b6a28f1518e39f2bb75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429385"
---
# <a name="adding-a-class-visual-c"></a>Agregar una clase (Visual C++)

Para agregar una clase en un proyecto de Visual C++, en el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto, haga clic en **Agregar** y después en **Clase**. Se abrirá el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md).

Cuando se agrega una clase, se debe especificar un nombre que sea distinto al de las clases que ya existen en MFC o ATL. Si se especifica un nombre que ya existe en alguna de esas bibliotecas, el IDE muestra un mensaje de error.

Si la convención de nomenclatura del proyecto requiere usar un nombre existente, solo se pueden cambiar las mayúsculas y minúsculas de una o varias letras en el nombre porque C++ distingue mayúsculas de minúsculas. Por ejemplo, aunque una clase no se puede denominar `CDocument`, se puede denominar `cdocument`.

## <a name="what-kind-of-class-do-you-want-to-add"></a>¿Qué tipo de clase quiere agregar?

En el cuadro de diálogo **Agregar clase**, cuando se expande el nodo **Visual C++** en el panel de la izquierda, se muestran varias agrupaciones de plantillas instaladas. Los grupos incluyen **CLR**, **ATL**, **MFC** y **C++**. Cuando se selecciona un grupo, en el panel central se muestra una lista de las plantillas disponibles en ese grupo. Cada plantilla contiene los archivos y el código fuente que son necesarios para una clase.

Para generar una clase nueva, seleccione una plantilla en el panel central, escriba un nombre para la clase en el cuadro **Nombre** y haga clic en **Agregar**. Se abrirá el **Asistente para agregar clases** para que pueda especificar opciones para la clase.

- Para obtener más información sobre cómo crear clases de MFC, vea [Clase MFC](../mfc/reference/adding-an-mfc-class.md).

- Para obtener más información sobre cómo crear clases de ATL, vea [Objeto simple ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
>  La plantilla **Agregar compatibilidad de ATL a MFC** no crea una clase, pero en su lugar, configura el proyecto para usar ATL. Para obtener más información, vea [Compatibilidad con ATL en un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Para hacer que una clase de C++ que no usa MFC, ATL ni CLR, use la plantilla **Clase de C++** del grupo de plantillas instaladas **C++**. Para obtener más información, vea [Agregar una clase genérica de C++](../ide/adding-a-generic-cpp-class.md).

Existen dos tipos de clases de C++ basadas en formularios. El primero, [CFormView (clase)](../mfc/reference/cformview-class.md), crea una clase de MFC. El segundo crea una clase de Windows Forms de CLR.

## <a name="see-also"></a>Vea también

[Creación de una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md)<br>
[Agregar clase (Cuadro de diálogo)](../ide/add-class-dialog-box.md)<br>
[Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)
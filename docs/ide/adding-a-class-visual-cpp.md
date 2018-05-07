---
title: Agregar una clase (Visual C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.adding
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14e16d8b5c15939adb792a96a828bafd07ba4041
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="adding-a-class-visual-c"></a>Agregar una clase (Visual C++)
Para agregar una clase en un proyecto de Visual C++, en **el Explorador de soluciones**, haga clic en el proyecto, haga clic en **agregar**y, a continuación, haga clic en **clase**. Se abrirá la [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md) cuadro de diálogo.  
  
 Cuando se agrega una clase, debe especificar un nombre que sea distinto de las clases que ya existen en MFC o ATL. Si especifica un nombre que ya existe en alguna de esas bibliotecas, el IDE muestra un mensaje de error.  
  
 Si el proyecto de convención de nomenclatura requiere usar un nombre existente, a continuación, solo puede cambiar el caso de una o varias letras en el nombre porque C++ distingue mayúsculas de minúsculas. Por ejemplo, aunque no se asigne un nombre a una clase `CDocument`, que se denomina `cdocument`.  
  
## <a name="what-kind-of-class-do-you-want-to-add"></a>¿Qué tipo de clase que desea agregar?  
 En el **Agregar clase** cuadro de diálogo, cuando se expande el **Visual C++** nodo en el panel izquierdo se muestran varias agrupaciones de plantillas instaladas. Los grupos incluyen **CLR**, **ATL**, **MFC**, y **C++**. Cuando se selecciona un grupo, se muestra una lista de las plantillas disponibles en ese grupo en el panel central. Cada plantilla contiene los archivos y el código fuente que son necesarios para una clase.  
  
 Para generar una nueva clase, seleccione una plantilla en el panel central, escriba un nombre para la clase en el **nombre** cuadro y haga clic en **agregar**. Se abrirá la **Asistente para agregar clases** para que pueda especificar opciones para la clase.  
  
-   Para obtener más información sobre cómo crear clases de MFC, vea [clase MFC](../mfc/reference/adding-an-mfc-class.md).  
  
-   Para obtener más información sobre cómo crear clases ATL, vea [objeto Simple ATL](../atl/reference/adding-an-atl-simple-object.md).  
  
> [!NOTE]
>  La plantilla **agregar compatibilidad con ATL a MFC** no crea una clase, pero en su lugar, configura el proyecto para utilizar ATL. Para obtener más información, consulte [compatibilidad con ATL en un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
 Para convertir una clase de C++ que no usa MFC, ATL ni CLR, use la **clases de C++** plantilla en el **C++** grupo de plantillas instaladas. Para obtener más información, consulte [agregar una clase genérica de C++](../ide/adding-a-generic-cpp-class.md).  
  
 Hay disponibles dos tipos de clases de C++ basadas en formularios. La primera de ellas, [clase CFormView](../mfc/reference/cformview-class.md) crea una clase MFC. La segunda crea una clase de formularios Windows Forms de CLR.  
  
## <a name="see-also"></a>Vea también  
 [Crear una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [Agregar cuadro de diálogo de clase](../ide/add-class-dialog-box.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)
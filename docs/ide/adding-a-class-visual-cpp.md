---
title: "Agregar una clase (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.classes.adding"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL (proyectos), agregar clases"
  - "clases [C++], agregar"
  - "clases [C++], crear"
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar una clase (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para agregar una clase en un proyecto de Visual C\+\+, en el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto, en **Agregar** y, a continuación, haga clic en **Clase**.  Se abrirá el cuadro de diálogo [Agregar clase \(Cuadro de diálogo\)](../ide/add-class-dialog-box.md).  
  
 Al agregar una clase, se debe especificar un nombre diferente de las clases que ya existen en MFC o ATL.  Si se especifica un nombre que ya existe en alguna de esas bibliotecas, Visual C\+\+ muestra un mensaje que indica que el nombre especificado está reservado.  
  
 Si la convención de nomenclatura de proyecto requiere utilizar un nombre existente, puede cambiar a mayúsculas una o varias letras del nombre porque Visual C\+\+ distingue entre mayúsculas y minúsculas.  Por ejemplo, aunque no puede denominar una clase `CDocument`, puede denominarla `cdocument`.  
  
## ¿Qué tipo de clase desea agregar?  
 En el cuadro de diálogo **Agregar clase**, cuando se expande el nodo **Visual C\+\+** en el panel de la izquierda se muestran varias agrupaciones de las plantillas instaladas.  Los grupos incluyen **CLR**, **ATL**, **MFC** y **C\+\+**.  Cuando se selecciona un grupo, una lista de las plantillas disponibles en ese grupo se muestra en el panel central.  Cada plantilla contiene los archivos y el código fuente que se requieren para una clase.  
  
 Para generar una nueva clase, seleccione una plantilla en el panel central, escriba un nombre para la clase en el cuadro **Nombre** y haga clic en **Agregar**.  Esto abre el **Asistente para agregar clases** para poder especificar opciones para la clase.  
  
-   Para obtener más información sobre cómo crear clases MFC, vea [MFC \(clase\)](../mfc/reference/adding-an-mfc-class.md).  
  
-   Para obtener más información sobre cómo crear clases ATL, vea [ATL Simple Object](../atl/reference/adding-an-atl-simple-object.md).  
  
> [!NOTE]
>  La plantilla **Agregar compatibilidad ATL a MFC** no crea una nueva clase sino que configura el proyecto para utilizar ATL.  Para obtener más información, vea [Compatibilidad con ATL en un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
 Para crear una clase de C\+\+ que no use MFC, ATL o CLR, use la plantilla **Clase de C\+\+** en el grupo de **C\+\+** de plantillas instaladas.  Para obtener más información, vea [Agregar una clase genérica de C\+\+](../ide/adding-a-generic-cpp-class.md).  
  
 Hay dos tipos de clases de C\+\+ basadas en formulario.  El primero, [CFormView Class](../mfc/reference/cformview-class.md), crea una clase MFC.  El segundo, Windows Forms, crea una clase CLR.  
  
## Vea también  
 [Crear una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [Agregar clase \(Cuadro de diálogo\)](../ide/add-class-dialog-box.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)
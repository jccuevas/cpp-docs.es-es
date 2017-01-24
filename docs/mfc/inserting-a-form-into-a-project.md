---
title: "Insertar un formulario en un proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "formularios, agregar a proyectos"
  - "Insertar nuevo (cuadro de diálogo)"
  - "insertar formularios"
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Insertar un formulario en un proyecto
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Formularios proporcionan un contenedor adecuado para los controles.  Es fácil insertar un formulario MFC\- basado en la aplicación mientras la aplicación admita las bibliotecas MFC.  
  
### Para insertar un formulario en el proyecto  
  
1.  En la vista de clases, seleccione el proyecto al que desea agregar el formulario, haga clic con el botón secundario del mouse.  
  
2.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
     Si el comando de **New Form** no está disponible, el proyecto se puede basar en Active Template Library \(ATL\).  Agregar un formulario a un proyecto ATL, debe [especifique ciertos valores](../atl/reference/application-settings-atl-project-wizard.md) al crear el proyecto.  
  
3.  De la carpeta de **MFC** , haga clic en **Clase MFC**.  
  
4.  Mediante el asistente para clases MFC, haga que la nueva clase deriva de [CFormView](../mfc/reference/cformview-class.md).  
  
 Visual C\+\+ agrega el formulario a la aplicación, ábralo en el editor de cuadros de diálogo para que pueda iniciar los controles y ejecución de la especificación del diseño general.  
  
 Puede realizar los pasos adicionales siguientes \(no aplicables para las aplicaciones diálogo\- basadas\):  
  
1.  Reemplace la función miembro de `OnUpdate` .  
  
2.  Implemente una función miembro para mover datos de la vista al documento.  
  
3.  Cree una función miembro de `OnPrint` .  
  
## Vea también  
 [Vistas de formulario](../mfc/form-views-mfc.md)
---
title: "Defining Member Variables for Dialog Controls | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "member variables, defining for controls"
  - "variables, dialog box control member variables"
  - "controls [C++], member variables"
  - "Dialog editor, defining member variables for controls"
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Defining Member Variables for Dialog Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para definir una variable miembro para cualquier control de cuadro de diálogo excepto los botones, puede utilizar el método siguiente.  
  
> [!NOTE]
>  Este artículo se aplica solo a los controles de cuadro de diálogo de un proyecto MFC.  Los proyectos ATL deben usar el nuevo cuadro de diálogo **Nuevos mensajes de Windows y controladores de eventos**.  
  
### Para definir una variable miembro para un control de cuadro de diálogo \(que no sea un botón\)  
  
1.  Seleccione un control en el [Editor de cuadros de diálogo](../mfc/dialog-editor.md).  
  
2.  Mientras presiona la tecla **Ctrl**, haga doble clic en el control de cuadro de diálogo.  
  
     Aparecerá el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md).  
  
3.  Escriba la información correspondiente en el asistente **Agregar variable miembro**.  Para obtener más información, vea [Intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md).  
  
4.  Haga clic en **Aceptar** para volver al Editor de cuadros de diálogo.  
  
    > [!TIP]
    >  Para saltar de un control de cuadro de diálogo a su controlador existente, haga doble clic en el control.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 También puede utilizar la ficha **Variables miembro** de **Asistente para clases MFC** para agregar nuevas variables miembro a una clase especificada y ver las que ya se han definido.  
  
 Requisitos  
  
 MFC  
  
## Vea también  
 [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)   
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Asistente para clases MFC](../mfc/reference/mfc-class-wizard.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)
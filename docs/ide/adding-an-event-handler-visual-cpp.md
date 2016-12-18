---
title: "Agregar un controlador de eventos (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.eventhandler.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controladores de eventos, agregar"
  - "MSBuild, propiedades"
  - "propiedades [Visual Studio], MSBuild"
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar un controlador de eventos (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Desde el editor de recursos, mediante el [Asistente para controladores de eventos](../ide/event-handler-wizard.md), es posible tanto agregar un nuevo controlador de eventos como editar un controlador de eventos existente para un control de cuadro de diálogo.  
  
 Es posible agregar un evento a la clase que implementa el cuadro de diálogo mediante la [ventana Propiedades](../Topic/Properties%20Window.md).  Si desea agregar el evento a una clase distinta de la del cuadro de diálogo, utilice el Asistente para controladores de eventos.  
  
### Para agregar un controlador de eventos a un control de cuadro de diálogo  
  
1.  Haga doble clic en el recurso de cuadro de diálogo de la [Vista de recursos](../windows/resource-view-window.md) para abrir el recurso de cuadro de diálogo que contiene el control en el [editor de cuadros de diálogo](../mfc/dialog-editor.md).  
  
2.  Haga clic con el botón secundario en el control para el que desea tratar el evento de notificación.  
  
3.  En el menú contextual, haga clic en **Agregar controlador de eventos** para abrir el Asistente para controladores de eventos.  
  
4.  Seleccione el evento en el cuadro **Tipo de mensaje** para agregarlo a la clase seleccionada en el cuadro **Lista de clases**.  
  
5.  Acepte el nombre predeterminado del cuadro **Nombre de controlador de funciones** o asigne un nombre de su elección.  
  
6.  Haga clic en **Agregar y editar** para agregar el controlador de eventos al proyecto y abra el editor de texto en la nueva función para agregar el código del controlador de eventos apropiado.  
  
     Si el tipo de mensaje seleccionado ya tiene un controlador de eventos para la clase seleccionada, el comando **Agregar y editar** no estará disponible, pero sí lo estará el comando **Editar código**.  Haga clic en **Editar código** para abrir el editor de texto en la función existente.  
  
 Como alternativa, puede agregar controladores de eventos desde la [ventana Propiedades](../Topic/Properties%20Window.md).  Vea [Agregar controladores de eventos para controles de cuadros de diálogo](../mfc/adding-event-handlers-for-dialog-box-controls.md) para obtener más información.  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)
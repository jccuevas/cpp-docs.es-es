---
title: "Agregar una variable miembro (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.classes.member.variable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "variables miembro"
  - "variables miembro, agregar"
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar una variable miembro (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede agregar una variable miembro a una clase mediante la Vista de clases.  Las variables miembro pueden estar destinadas al [intercambio y validación de datos](../mfc/dialog-data-exchange-and-validation.md) o pueden ser de uso genérico.  El asistente para variables miembro de datos está diseñado específicamente para tomar la información correspondiente y usarla para insertar elementos en los archivos de código fuente en la ubicación adecuada.  Se puede agregar una variable miembro desde el [Editor de cuadros de diálogo](../mfc/dialog-editor.md) en la [Vista de recursos](../windows/resource-view-window.md) o desde la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Al diseñar e implementar un cuadro de diálogo, puede resultar más eficaz usar el Editor de cuadros de diálogo para agregar los controles e implementar a continuación las variables miembro correspondientes.  
  
### Para agregar una variable miembro de un control de cuadro de diálogo en la Vista de recursos mediante el Asistente para agregar variables miembro  
  
1.  En la Vista de recursos, expanda el nodo del proyecto y el nodo Dialog para mostrar la lista de cuadros de diálogo que contiene.  
  
2.  Haga doble clic en el cuadro de diálogo al que desee agregar la variable miembro para abrirlo en el Editor de cuadros de diálogo.  
  
3.  En el cuadro de diálogo abierto en el Editor, haga clic con el botón secundario del mouse en el control al que desee agregar la variable miembro.  
  
4.  En el menú contextual, haga clic en **Agregar variable** para mostrar el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Ya se proporciona un valor predeterminado en **Id. de control**.  
  
5.  Indique la información correspondiente en los cuadros del asistente.  Vea [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
6.  Haga clic en **Finalizar** para agregar el código de definición e implementación al proyecto y cierre el asistente.  
  
### Para agregar una variable miembro desde la Vista de clases mediante el Asistente para agregar variables miembro  
  
1.  En la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), expanda el nodo del proyecto para mostrar las clases del proyecto.  
  
2.  Haga clic con el botón secundario del mouse en la clase a la cual desee agregar una variable.  
  
3.  En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar variable** para mostrar el Asistente para agregar variables miembro.  
  
4.  Indique la información correspondiente en los cuadros del asistente.  Vea [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para obtener más detalles.  
  
5.  Haga clic en **Finalizar** para agregar el código de definición e implementación al proyecto y cierre el asistente.  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)
---
title: Agregar una Variable miembro (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.classes.member.variable
dev_langs: C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52d98e3eae6e468db7c2737efac8c2b7ab04abd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-member-variable--visual-c"></a>Agregar una variable miembro (Visual C++)
Puede agregar una variable miembro a una clase mediante la vista de clases. Variables de miembro pueden ser para [intercambio y validación de datos](../mfc/dialog-data-exchange-and-validation.md), o pueden ser genéricos. El Asistente para variables de miembro de datos está diseñado específicamente para tomar la información correspondiente y usarla para insertar elementos en los archivos de origen en las ubicaciones adecuadas. Puede agregar una variable miembro de la [editor de cuadro de diálogo](../windows/dialog-editor.md) en [vista de recursos](../windows/resource-view-window.md), o de [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Cuando diseñe e implementar un cuadro de diálogo, le resultará más eficaz utilizar el cuadro de diálogo editor para agregar los controles de cuadro de diálogo y, después, implementar las variables de miembro de los controles.  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Para agregar una variable miembro para un control de cuadro de diálogo en la vista de recursos mediante el Asistente para agregar variables miembro  
  
1.  En la vista de recursos, expanda el nodo del proyecto y el nodo de cuadro de diálogo para mostrar la lista de cuadros de diálogo del proyecto.  
  
2.  Haga doble clic en el cuadro de diálogo en el que desea agregar la variable miembro para abrirlo en el editor de cuadro de diálogo.  
  
3.  En el cuadro de diálogo que se muestra en el editor de cuadro de diálogo, haga clic en el control al que desea agregar la variable miembro.  
  
4.  En el menú contextual, haga clic en **agregar Variable** para mostrar la [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Ya se proporciona un valor predeterminado en **Id. de Control**.  
  
5.  Proporcione la información en los cuadros apropiados del asistente. Vea [controles de cuadro de diálogo y tipos de Variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
6.  Haga clic en **finalizar** para agregar el código de definición e implementación al proyecto y cerrar el asistente.  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Para agregar una variable miembro de la vista de clases mediante el Asistente para agregar variables miembro  
  
1.  En [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), expanda el nodo del proyecto para mostrar las clases del proyecto.  
  
2.  Haga clic en la clase a la que desea agregar una variable.  
  
3.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **agregar Variable** para mostrar el Asistente para agregar variables miembro.  
  
4.  Proporcione la información en los cuadros apropiados del asistente. Vea [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para obtener más información.  
  
5.  Haga clic en **finalizar** para agregar el código de definición e implementación al proyecto y cerrar el asistente.  
  
## <a name="see-also"></a>Vea también  
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)
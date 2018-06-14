---
title: Agregar una variable miembro (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa2a8ef8f7bcdc2d90893acdad98705c9588a5d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325736"
---
# <a name="adding-a-member-variable--visual-c"></a>Agregar una variable miembro (Visual C++)
Se puede agregar una variable miembro a una clase mediante la Vista de clases. Las variables miembro pueden ser para [intercambio y validación de datos](../mfc/dialog-data-exchange-and-validation.md), o bien pueden ser genéricas. El Asistente para variables miembro de datos está diseñado específicamente para tomar la información correspondiente y usarla para insertar elementos en los archivos de código fuente en las ubicaciones adecuadas. Una variable miembro se puede agregar desde el [Editor de cuadros de diálogo](../windows/dialog-editor.md) en la [Vista de recursos](../windows/resource-view-window.md), o bien desde la [Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Cuando diseñe e implemente un cuadro de diálogo, es posible que le resulte más eficaz usar el Editor de cuadros de diálogo para agregar los controles de cuadro de diálogo y, después, implementar las variables miembro de los controles.  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Para agregar una variable miembro para un control de cuadro de diálogo en la Vista de recursos mediante el Asistente para agregar variables miembro  
  
1.  En la Vista de recursos, expanda el nodo del proyecto y el nodo Cuadro de diálogo para mostrar la lista de cuadros de diálogo del proyecto.  
  
2.  Haga doble clic en el cuadro de diálogo al que quiera agregar la variable miembro para abrirlo en el Editor de cuadros de diálogo.  
  
3.  En el cuadro de diálogo que se muestra en el Editor de cuadros de diálogo, haga clic con el botón derecho en el control al que quiera agregar la variable miembro.  
  
4.  En el menú contextual, haga clic en **Agregar variable** para mostrar el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Ya se proporciona un valor predeterminado en **Id. de control**.  
  
5.  Proporcione la información en los cuadros apropiados del asistente. Vea [Controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.  
  
6.  Haga clic en **Finalizar** para agregar la definición y el código de implementación al proyecto y cerrar el asistente.  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Para agregar una variable miembro desde la Vista de clases mediante el Asistente para agregar variables miembro  
  
1.  En la [Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), expanda el nodo del proyecto para mostrar las clases del proyecto.  
  
2.  Haga clic con el botón derecho en la clase a la que quiera agregar una variable.  
  
3.  En el menú contextual, haga clic en **Agregar** y después en **Agregar variable** para mostrar el Asistente para agregar variables miembro.  
  
4.  Proporcione la información en los cuadros apropiados del asistente. Vea [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para obtener más información.  
  
5.  Haga clic en **Finalizar** para agregar la definición y el código de implementación al proyecto y cerrar el asistente.  
  
## <a name="see-also"></a>Vea también  
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Adición de un controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)
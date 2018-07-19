---
title: Definir Variables miembro para los controles de cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog editor, defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8ba8fc95290ecb90557203be2b6ab4cce18b91e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873841"
---
# <a name="defining-member-variables-for-dialog-controls"></a>Definir variables miembro para los controles de cuadro de diálogo
Para definir una variable miembro para cualquier control de cuadro de diálogo excepto los botones, puede utilizar el método siguiente.  
  
> [!NOTE]
>  Este artículo se aplica solo a los controles de cuadro de diálogo de un proyecto MFC. Los proyectos ATL deben utilizar el **nuevos mensajes de Windows y controladores de eventos** cuadro de diálogo.  
  
### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Para definir una variable miembro para un control de cuadro de diálogo (que no sea un botón)  
  
1.  En el [editor de cuadro de diálogo](../windows/dialog-editor.md), seleccione un control.  
  
2.  Mientras presiona la **CTRL** clave, haga doble clic en el control de cuadro de diálogo.  
  
     El [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) aparece.  
  
3.  Escriba la información correspondiente en el **agregar variables miembro** asistente. Para obtener más información, consulte [intercambio de datos de cuadros de diálogo](../mfc/dialog-data-exchange.md).  
  
4.  Haga clic en **Aceptar** para volver al editor de cuadro de diálogo.  
  
    > [!TIP]
    >  Para saltar de un control de cuadro de diálogo a su controlador existente, haga doble clic en el control.  
  

  
 También puede usar el **Variables de miembro** ficha **Asistente para clases MFC** para agregar nuevas variables miembro a una clase especificada y verlos que ya se ha definido.  
  
 Requisitos  
  
 MFC  
  
## <a name="see-also"></a>Vea también  
 [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)   
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Asistente para clases MFC](../mfc/reference/mfc-class-wizard.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función Virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md)


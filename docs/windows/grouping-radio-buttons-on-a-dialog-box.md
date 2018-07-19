---
title: Agrupar botones de Radio en un cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.grouping
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls, grouping radio buttons
- grouping controls
- radio buttons, grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aee3245a65ccdccc32b40c313eecdd45cb3ea8bf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879333"
---
# <a name="grouping-radio-buttons-on-a-dialog-box"></a>Agrupar botones de opción en un cuadro de diálogo
Al agregar botones de radio a un cuadro de diálogo, trátelos como grupo, estableciendo una propiedad Grupo en la ventana Propiedades para el primer botón del grupo. Después, aparecerá un id. de control para ese botón de opción en el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), lo que le permite agregar una variable miembro para el grupo de botones de radio.  
  
 Puede tener más de un grupo de botones de radio en un cuadro de diálogo y se debe agregar cada grupo mediante el siguiente procedimiento.  
  
### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Para agregar un grupo de botones de radio a un cuadro de diálogo  
  
1.  Seleccione el control de botón de radio en la [ventana del cuadro de herramientas](/visualstudio/ide/reference/toolbox) y haga clic en la ubicación del cuadro de diálogo donde quiere colocar el control.  
  
2.  Repita el paso 1 para agregar tantos botones de radio como necesite. Asegúrese de que los botones de radio del grupo sean consecutivos en el orden de tabulación (para más información, vea [Cambiar el orden de tabulación de los controles](../windows/changing-the-tab-order-of-controls.md)).  
  
3.  En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), establezca la propiedad **Grupo** del *primer* botón de radio en el orden de tabulación en **True**.  
  
     Al cambiar la propiedad **Grupo** a **True** se agrega el estilo WS_GROUP a la entrada del botón en el objeto de diálogo del script de recursos y se asegura que un usuario solo puede seleccionar un botón de radio cada vez en el grupo de botones (cuando el usuario hace clic en un botón de radio, se borran los demás miembros del grupo).  
  
    > [!NOTE]
    >  Solo el primer botón de radio del grupo debe tener la propiedad **Grupo** establecida en **True**. Si dispone de otros controles que no forman parte del grupo de botones, establezca la propiedad **Grupo** del primer control *que se encuentra fuera del grupo* también en **True** . Para identificar rápidamente el primer control fuera del grupo, presione CTRL+D para ver el orden de tabulación.  
  
### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Para agregar una variable miembro para el grupo de botones de radio  
  
1.  Haga clic con el botón secundario en el primer control de botón de radio en el orden de tabulación (el control dominante y el otro con la propiedad **Grupo** establecida en True).  
  
2.  Elija **Agregar variable** en el menú contextual.  
  
3.  En el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), active la casilla **Variable de control** y luego seleccione el botón de radio **Valor** .  
  
4.  En el cuadro **Nombre de variable** , escriba un nombre para la nueva variable miembro.  
  
5.  En el cuadro de lista **Tipo de variable** , seleccione **int** o escriba **int**.  
  
6.  Ahora puede modificar el código para especificar qué botón de radio debe aparecer seleccionado. Por ejemplo,m_radioBox1 = 0 selecciona el primer botón de radio del grupo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Organización de los controles de cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)


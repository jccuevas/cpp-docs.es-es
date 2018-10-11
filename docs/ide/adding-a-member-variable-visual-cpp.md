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
ms.openlocfilehash: ec9409067793da0e0a89be668f57e86588bdc2d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447328"
---
# <a name="adding-a-member-variable--visual-c"></a>Agregar una variable miembro (Visual C++)

Se puede agregar una variable miembro a una clase mediante la Vista de clases. Las variables miembro pueden ser para [intercambio y validación de datos](../mfc/dialog-data-exchange-and-validation.md), o bien pueden ser genéricas. El Asistente para variables miembro de datos está diseñado específicamente para tomar la información correspondiente y usarla para insertar elementos en los archivos de código fuente en las ubicaciones adecuadas. Una variable miembro se puede agregar desde el [Editor de cuadros de diálogo](../windows/dialog-editor.md) en la [Vista de recursos](../windows/resource-view-window.md), o bien desde la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
>  Cuando diseñe e implemente un cuadro de diálogo, es posible que le resulte más eficaz usar el Editor de cuadros de diálogo para agregar los controles de cuadro de diálogo y, después, implementar las variables miembro de los controles.

### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Para agregar una variable miembro para un control de cuadro de diálogo en la Vista de recursos mediante el Asistente para agregar variables miembro

1. En la Vista de recursos, expanda el nodo del proyecto y el nodo Cuadro de diálogo para mostrar la lista de cuadros de diálogo del proyecto.

1. Haga doble clic en el cuadro de diálogo al que quiera agregar la variable miembro para abrirlo en el Editor de cuadros de diálogo.

1. En el cuadro de diálogo que se muestra en el Editor de cuadros de diálogo, haga clic con el botón derecho en el control al que quiera agregar la variable miembro.

1. En el menú contextual, haga clic en **Agregar variable** para mostrar el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md).

   > [!NOTE]
   > Ya se proporciona un valor predeterminado en **Id. de control**.

1. Proporcione la información en los cuadros apropiados del asistente. Vea [Controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md) para obtener más información.

1. Haga clic en **Finalizar** para agregar la definición y el código de implementación al proyecto y cerrar el asistente.

### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Para agregar una variable miembro desde la Vista de clases mediante el Asistente para agregar variables miembro

1. En la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code), expanda el nodo del proyecto para mostrar las clases del proyecto.

1. Haga clic con el botón derecho en la clase a la que quiera agregar una variable.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar variable** para mostrar el Asistente para agregar variables miembro.

1. Proporcione la información en los cuadros apropiados del asistente. Vea [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para obtener más información.

1. Haga clic en **Finalizar** para agregar la definición y el código de implementación al proyecto y cerrar el asistente.

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Agregar una clase](../ide/adding-a-class-visual-cpp.md)<br>
[Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)<br>
[Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)
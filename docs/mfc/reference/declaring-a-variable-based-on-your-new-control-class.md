---
title: Declarar una variable basada en una clase de control nueva
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: b3b1a168619c1c111db3e71e1a9562d441cc710d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302083"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Declarar una variable basada en una clase de control nueva

Una vez haya creado una clase de control MFC, puede declarar una variable basada en él. Para proporcionar un contexto para la nueva variable, debe abrir el editor de cuadro de diálogo y editar el cuadro de diálogo en el que desea utilizar el control reutilizable. Además, el cuadro de diálogo ya debe tener una clase asociada a él. Para obtener información acerca de cómo utilizar el editor de cuadro de diálogo, vea [Editor de cuadro de diálogo](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Para declarar una variable basada en una clase reutilizable

1. Mientras edita el cuadro de diálogo, arrastre un control del mismo tipo como clase base del nuevo control desde la barra de herramientas de controles en el cuadro de diálogo.

1. Coloque el puntero del mouse sobre el control arrastrado.

1. Mientras se presiona la tecla CTRL, haga doble clic en el control.

   El [agregar variables miembro](../../ide/add-member-variable-wizard.md) aparece el cuadro de diálogo.

1. En el **acceso** , seleccione el acceso correcto para el control.

1. Haga clic en el **variable de Control** casilla de verificación.

1. En el **nombre de Variable** , escriba un nombre.

1. En **categoría**, haga clic en **Control**.

1. En el **Id. de Control** lista, elija el control que ha agregado. El **tipo de Variable** lista debe mostrar el tipo de variable correcto y el **tipo de Control** cuadro debe mostrar el tipo de control correcto.

9. En el **comentario** , agregue cualquier comentario que desee que aparezca en el código.

10. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

[Asignación de mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)

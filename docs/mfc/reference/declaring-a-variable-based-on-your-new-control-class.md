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
ms.openlocfilehash: 994f81524001a80d1cf0dd3783b9de742d61e84d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365844"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Declarar una variable basada en una clase de control nueva

Una vez que haya creado una clase de control MFC, puede declarar una variable basada en ella. Para proporcionar un contexto para la nueva variable, debe abrir el editor de cuadros de diálogo y editar el cuadro de diálogo en el que desea utilizar el control reutilizable. Además, el cuadro de diálogo ya debe tener una clase asociada. Para obtener información sobre el uso del editor de cuadros de diálogo, consulte [Editor de cuadros](../../windows/dialog-editor.md)de diálogo .

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Para declarar una variable basada en la clase reutilizable

1. Al editar el cuadro de diálogo, arrastre un control del mismo tipo que la clase base del nuevo control desde la barra de herramientas Controles hasta el cuadro de diálogo.

1. Coloque el puntero del mouse sobre el control caído.

1. Mientras presiona la tecla CTRL, haga doble clic en el control.

   Aparece el cuadro de diálogo [Agregar variable miembro.](../../ide/add-member-variable-wizard.md)

1. En el cuadro **Acceso,** seleccione el acceso correcto para el control.

1. Haga clic en la casilla de verificación Variable de **control.**

1. En el cuadro **Nombre** de variable, escriba un nombre.

1. En **Categoría**, haga clic en **Control**.

1. En la lista **Identificador** de control, elija el control que agregó. La lista **Tipo** de variable debe mostrar el tipo de variable correcto y el cuadro **Tipo** de control debe mostrar el tipo de control correcto.

1. En el cuadro **Comentario,** agregue cualquier comentario que desee que aparezca en el código.

1. Haga clic en **OK**.

## <a name="see-also"></a>Consulte también

[Asignación de mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigate-code-cpp.md)

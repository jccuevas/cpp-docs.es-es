---
title: Declarar una Variable basada en su nueva clase de Control | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2e5e91465df0c3e7608b949c6e1f4b8dfc80bc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064152"
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

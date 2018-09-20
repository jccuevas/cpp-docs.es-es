---
title: Definir Variables miembro para controles de cuadro de diálogo (C++) | Microsoft Docs
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
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa4d894fb3fc436abab84bfee11199f59bd66f78
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402400"
---
# <a name="defining-member-variables-for-dialog-controls-c"></a>Definir Variables miembro para controles de cuadro de diálogo (C++)

Para definir una variable miembro para cualquier control de cuadro de diálogo excepto los botones, puede utilizar el método siguiente.

> [!NOTE]
> Este artículo se aplica solo a los controles de cuadro de diálogo de un proyecto MFC. Los proyectos ATL deben usar el **nuevos mensajes de Windows y controladores de eventos** cuadro de diálogo.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Para definir una variable miembro para un control de cuadro de diálogo (que no sea un botón)

1. En el [editor de cuadro de diálogo](../windows/dialog-editor.md), seleccione un control.

2. Al presionar el **Ctrl** clave, haga doble clic en el control de cuadro de diálogo.

   El [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) aparece.

3. Escriba la información correspondiente en el **agregar variables miembro** asistente. Para obtener más información, consulte [intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md).

4. Haga clic en **Aceptar** para volver a la **diálogo** editor.

   > [!TIP]
   > Para saltar de un control de cuadro de diálogo a su controlador existente, haga doble clic en el control.

También puede usar el **Variables miembro** pestaña **Asistente para clases MFC** para agregar nuevas variables miembro a una clase especificada y verlos que ya se han definido.

## <a name="requirements"></a>Requisitos

MFC

## <a name="see-also"></a>Vea también

[Asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Asistente para clases MFC](../mfc/reference/mfc-class-wizard.md)<br/>
[Agregar una clase](../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función Virtual](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)
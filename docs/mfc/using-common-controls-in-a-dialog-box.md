---
title: Usar controles comunes en un cuadro de diálogo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff5c3f28a47eb4e1810f046a242f6170c537bf2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054941"
---
# <a name="using-common-controls-in-a-dialog-box"></a>Usar controles comunes en un cuadro de diálogo

Se pueden usar los controles comunes de Windows en [cuadros de diálogo](../mfc/dialog-boxes.md), vistas, vistas de registros y cualquier otra ventana basada en una plantilla de cuadro de diálogo de formulario. El siguiente procedimiento, con cambios menores, funcionará también para formularios.

## <a name="procedures"></a>Procedimientos

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>Para utilizar un control común en un cuadro de diálogo

1. Colocar el control en la plantilla de cuadro de diálogo [con el editor de cuadro de diálogo](../mfc/using-the-dialog-editor-to-add-controls.md).

1. Agregar una variable miembro que representa el control a la clase de cuadro de diálogo. En el **agregar variables miembro** cuadro de diálogo, verificación **variable de Control** y asegúrese de que **Control** está seleccionada para la **categoría**.

1. Si este control común es proporcionar una entrada al programa, declare miembros adicionales variable(s) en la clase de cuadro de diálogo para administrarlos valores de entrada.

    > [!NOTE]
    >  Puede agregar estas variables de miembro mediante el menú contextual en la vista de clases (vea [agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md)).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) para la clase de cuadro de diálogo, establezca las condiciones iniciales para el control común. Usa la variable miembro creada en el paso anterior, utilice las funciones miembro para establecer el valor inicial y otras opciones. Ver las siguientes descripciones de los controles para obtener más información sobre los valores.

   También puede usar [intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md) (DDX) para inicializar los controles en un cuadro de diálogo.

1. En los controladores para los controles en el cuadro de diálogo, utilice la variable miembro para manipular el control. Consulte las siguientes descripciones de los controles para obtener más información sobre los métodos.

    > [!NOTE]
    >  La variable miembro existirá solo mientras exista el mismo cuadro de diálogo. No podrá consultar el control de valores de entrada después de que se ha cerrado el cuadro de diálogo. Para trabajar con valores de entrada de un control común, invalidar `OnOK` en la clase de cuadro de diálogo. En la invalidación, el control de valores de entrada de consulta y almacenar esos valores en variables de miembro de la clase de cuadro de diálogo.

    > [!NOTE]
    >  También puede usar el intercambio de datos de cuadro de diálogo para establecer o recuperar los valores de los controles en un cuadro de diálogo.

## <a name="remarks"></a>Comentarios

La adición de algunos controles comunes a un cuadro de diálogo hará que el cuadro de diálogo ya no funcione. Consulte [agregar controles a un cuadro de diálogo, el cuadro de diálogo dejado de funcionar](../windows/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md) para obtener más información sobre cómo controlar esta situación.

## <a name="what-do-you-want-to-do"></a>Qué quieres hacer

- [Agregar controles a un cuadro de diálogo a mano en lugar de con el editor de cuadro de diálogo](../mfc/adding-controls-by-hand.md)

- [Derivar mi control de uno de los controles comunes de Windows estándares](../mfc/deriving-controls-from-a-standard-control.md)

- [Utilizar un control común como ventana secundaria](../mfc/using-a-common-control-as-a-child-window.md)

- [Recibir mensajes de notificación de un control](../mfc/receiving-notification-from-common-controls.md)

- [Usar el intercambio de datos de cuadro de diálogo (DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>Vea también

[Creación y uso de controles](../mfc/making-and-using-controls.md)<br/>
[Controles](../mfc/controls-mfc.md)


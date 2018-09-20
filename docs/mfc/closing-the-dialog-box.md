---
title: Cierre el cuadro de diálogo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9ad4b8af63b68912c232767bf1fd14070fda261
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409056"
---
# <a name="closing-the-dialog-box"></a>Cerrar el cuadro de diálogo

Cuadro de diálogo modal se cierra cuando el usuario elige uno de sus botones, normalmente el botón Aceptar o el botón Cancelar. Si elige el botón Aceptar o cancelar, Windows enviar el objeto de cuadro de diálogo un **BN_CLICKED** mensaje de notificación de control con el botón del identificador, ya sea **IDOK** o **IDCANCEL**. `CDialog` proporciona funciones de controlador de valor predeterminado para estos mensajes: `OnOK` y `OnCancel`. La llamada de controladores de forma predeterminada el `EndDialog` función miembro para cerrar el cuadro de diálogo. También puede llamar a `EndDialog` desde su propio código. Para obtener más información, consulte el [EndDialog](../mfc/reference/cdialog-class.md#enddialog) función miembro de clase `CDialog` en el *referencia de MFC*.

Para organizar el cierre y la eliminación de un cuadro de diálogo no modal, invalidar `PostNcDestroy` e invocar el **eliminar** operador en el **esto** puntero. [Destruir el cuadro de diálogo](../mfc/destroying-the-dialog-box.md) explica lo que sucede a continuación.

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)


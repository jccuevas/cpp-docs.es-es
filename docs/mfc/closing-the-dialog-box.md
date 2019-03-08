---
title: Cerrar el cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 07e4159eccde1fab89d4a5ffadee4e6d11fc20f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302590"
---
# <a name="closing-the-dialog-box"></a>Cerrar el cuadro de diálogo

Cuadro de diálogo modal se cierra cuando el usuario elige uno de sus botones, normalmente el botón Aceptar o el botón Cancelar. Si elige el botón Aceptar o cancelar, Windows enviar el objeto de cuadro de diálogo un **BN_CLICKED** mensaje de notificación de control con el botón del identificador, ya sea **IDOK** o **IDCANCEL**. `CDialog` proporciona funciones de controlador de valor predeterminado para estos mensajes: `OnOK` y `OnCancel`. La llamada de controladores de forma predeterminada el `EndDialog` función miembro para cerrar el cuadro de diálogo. También puede llamar a `EndDialog` desde su propio código. Para obtener más información, consulte el [EndDialog](../mfc/reference/cdialog-class.md#enddialog) función miembro de clase `CDialog` en el *referencia de MFC*.

Para organizar el cierre y la eliminación de un cuadro de diálogo no modal, invalidar `PostNcDestroy` e invocar el **eliminar** operador en el **esto** puntero. [Destruir el cuadro de diálogo](../mfc/destroying-the-dialog-box.md) explica lo que sucede a continuación.

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

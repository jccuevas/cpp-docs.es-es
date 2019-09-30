---
title: Cerrar el cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 48ea954552b3ea9aa7193a47fc2a66d731312d77
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685373"
---
# <a name="closing-the-dialog-box"></a>Cerrar el cuadro de diálogo

Un cuadro de diálogo modal se cierra cuando el usuario elige uno de sus botones, normalmente el botón Aceptar o el botón Cancelar. Al elegir el botón Aceptar o cancelar, Windows envía al objeto de cuadro de diálogo un mensaje de notificación de control **BN_CLICKED** con el identificador del botón, **IDOK** o **IDCANCEL**. `CDialog` proporciona funciones de controlador predeterminadas para estos mensajes: `OnOK` y `OnCancel`. Los controladores predeterminados llaman a la función miembro `EndDialog` para cerrar la ventana de cuadro de diálogo. También puede llamar a `EndDialog` desde su propio código. Para obtener más información, vea la función miembro [EndDialog](../mfc/reference/cdialog-class.md#enddialog) de la clase `CDialog` en la *referencia de MFC*.

Para organizar el cierre y la eliminación de un cuadro de diálogo no modal, invalide `PostNcDestroy` e invoque el operador **Delete** en el puntero **this** . [Al destruir el cuadro de diálogo](../mfc/destroying-the-dialog-box.md) se explica lo que ocurre a continuación.

## <a name="see-also"></a>Vea también

[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)

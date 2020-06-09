---
title: Cerrar el cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: a695a8e331eb8a4f22394deb65857bf93ecab41e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617208"
---
# <a name="closing-the-dialog-box"></a>Cerrar el cuadro de diálogo

Un cuadro de diálogo modal se cierra cuando el usuario elige uno de sus botones, normalmente el botón Aceptar o el botón Cancelar. Al elegir el botón Aceptar o cancelar, Windows envía al objeto de cuadro de diálogo un **BN_CLICKED** mensaje de notificación de control con el identificador del botón, **IDOK** o **IDCANCEL**. `CDialog`proporciona funciones de controlador predeterminadas para estos mensajes: `OnOK` y `OnCancel` . Los controladores predeterminados llaman `EndDialog` a la función miembro para cerrar la ventana de diálogo. También puede llamar a `EndDialog` desde su propio código. Para obtener más información, vea la función miembro [EndDialog](reference/cdialog-class.md#enddialog) de `CDialog` la clase en la *referencia de MFC*.

Para organizar el cierre y la eliminación de un cuadro de diálogo no modal, invalide `PostNcDestroy` e invoque el operador **Delete** en el puntero **this** . [Al destruir el cuadro de diálogo](destroying-the-dialog-box.md) se explica lo que ocurre a continuación.

## <a name="see-also"></a>Consulte también

[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)

---
title: Crear cuadros de diálogo modales
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: 5de6eeb616f32c7b8829d827988a972e41658530
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174099"
---
# <a name="creating-modal-dialog-boxes"></a>Crear cuadros de diálogo modales

Para crear un cuadro de diálogo modal, llame a cualquiera de los dos constructores públicos declarados en [CDialog](../mfc/reference/cdialog-class.md). A continuación, llame el objeto de cuadro de diálogo [DoModal](../mfc/reference/cdialog-class.md#domodal) función miembro para mostrar el cuadro de diálogo y administrar la interacción con él hasta que el usuario elige Aceptar o Cancelar. Esta administración por `DoModal` es lo que hace que el cuadro de diálogo modal. En los cuadros de diálogo modal, `DoModal` carga el recurso de cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

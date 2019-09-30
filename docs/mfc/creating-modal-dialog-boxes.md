---
title: Crear cuadros de diálogo modales
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed0fe3b7ef8aeddea01f573bfe8e1c01a6b5b443
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685675"
---
# <a name="creating-modal-dialog-boxes"></a>Crear cuadros de diálogo modales

Para crear un cuadro de diálogo modal, llame a cualquiera de los dos constructores públicos declarados en [CDialog](../mfc/reference/cdialog-class.md). Después, llame a la función miembro [DoModal](../mfc/reference/cdialog-class.md#domodal) del objeto de cuadro de diálogo para mostrar el cuadro de diálogo y administrar la interacción con él hasta que el usuario elija Aceptar o cancelar. Esta administración `DoModal` es lo que hace que el cuadro de diálogo sea modal. En los cuadros de diálogo modales, `DoModal` carga el recurso de cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)

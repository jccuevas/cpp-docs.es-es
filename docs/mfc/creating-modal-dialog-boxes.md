---
title: Crear cuadros de diálogo modales
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed7cc94982a46e542a5174d4d46b8013cc84ffa4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622981"
---
# <a name="creating-modal-dialog-boxes"></a>Crear cuadros de diálogo modales

Para crear un cuadro de diálogo modal, llame a cualquiera de los dos constructores públicos declarados en [CDialog](reference/cdialog-class.md). Después, llame a la función miembro [DoModal](reference/cdialog-class.md#domodal) del objeto de cuadro de diálogo para mostrar el cuadro de diálogo y administrar la interacción con él hasta que el usuario elija Aceptar o cancelar. Esta administración de `DoModal` es lo que hace que el cuadro de diálogo sea modal. En los cuadros de diálogo modales, `DoModal` carga el recurso de cuadro de diálogo.

## <a name="see-also"></a>Consulte también

[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)

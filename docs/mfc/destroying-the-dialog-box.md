---
title: Destruir el cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: 84ae5b336bb8eeac4f8ab7b6e5b9f00246f9ca15
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262004"
---
# <a name="destroying-the-dialog-box"></a>Destruir el cuadro de diálogo

Cuadros de diálogo modales normalmente se crean en el marco de pila y se destruyen cuando finaliza la función que los creó. Se llama al destructor del objeto de cuadro de diálogo cuando el objeto queda fuera del ámbito.

Cuadros de diálogo no modal normalmente se crean y que pertenecen a una ventana de vista o el marco primario: ventana de marco principal de la aplicación o una ventana de marco de documento. El valor predeterminado [OnClose](../mfc/reference/cwnd-class.md#onclose) llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), que destruye la ventana de cuadro de diálogo. Si el cuadro de diálogo permanece independiente, sin punteros o otra semántica de propiedad especial, se debe reemplazar [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) para destruir el objeto de cuadro de diálogo de C++. También debe reemplazar [OnCancel](../mfc/reference/cdialog-class.md#oncancel) y llamar a `DestroyWindow` desde dentro de él. Si no es así, el propietario del cuadro de diálogo debe destruir el objeto de C++ cuando ya no es necesario.

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

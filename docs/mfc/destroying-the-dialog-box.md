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
ms.openlocfilehash: 8b407c6e832dde7a5865146e7cc12d1840d3234a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685853"
---
# <a name="destroying-the-dialog-box"></a>Destruir el cuadro de diálogo

Los cuadros de diálogo modales se crean normalmente en el marco de pila y se destruyen cuando finaliza la función que los creó. Se llama al destructor del objeto de cuadro de diálogo cuando el objeto sale del ámbito.

Normalmente, los cuadros de diálogo no modales se crean y son propiedad de una vista primaria o una ventana de marco: la ventana de marco principal de la aplicación o una ventana de marco de documento. El controlador [OnClose](../mfc/reference/cwnd-class.md#onclose) predeterminado llama a [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), que destruye la ventana del cuadro de diálogo. Si el cuadro de diálogo es independiente, sin punteros a él u otra semántica de propiedad especial, debe invalidar [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) para destruir el C++ objeto de cuadro de diálogo. También debe invalidar [OnCancel](../mfc/reference/cdialog-class.md#oncancel) y llamar a `DestroyWindow` desde dentro. Si no es así, el propietario del cuadro de diálogo debería C++ destruir el objeto cuando ya no sea necesario.

## <a name="see-also"></a>Vea también

[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)

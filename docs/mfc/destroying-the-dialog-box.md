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
ms.openlocfilehash: 9b1244b03dc3f6f418730dd782050448f3bf8934
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621918"
---
# <a name="destroying-the-dialog-box"></a>Destruir el cuadro de diálogo

Los cuadros de diálogo modales se crean normalmente en el marco de pila y se destruyen cuando finaliza la función que los creó. Se llama al destructor del objeto de cuadro de diálogo cuando el objeto sale del ámbito.

Normalmente, los cuadros de diálogo no modales se crean y son propiedad de una vista primaria o una ventana de marco: la ventana de marco principal de la aplicación o una ventana de marco de documento. El controlador [OnClose](reference/cwnd-class.md#onclose) predeterminado llama a [DestroyWindow](reference/cwnd-class.md#destroywindow), que destruye la ventana del cuadro de diálogo. Si el cuadro de diálogo es independiente, sin punteros a él u otra semántica de propiedad especial, debe invalidar [PostNcDestroy](reference/cwnd-class.md#postncdestroy) para destruir el objeto de cuadro de diálogo de C++. También debe invalidar [OnCancel](reference/cdialog-class.md#oncancel) y llamar a `DestroyWindow` desde dentro. Si no es así, el propietario del cuadro de diálogo debe destruir el objeto de C++ cuando ya no sea necesario.

## <a name="see-also"></a>Consulte también

[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)

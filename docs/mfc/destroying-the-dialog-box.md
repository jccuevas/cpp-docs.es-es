---
title: "Destruir el cuadro de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b1b6c94c4c7efe3bc3300d6c8c5c34fbe890fb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-the-dialog-box"></a>Destruir el cuadro de diálogo
Cuadros de diálogo modales normalmente se crean en el marco de pila y se destruyen cuando finaliza la función que los creó. Se llama al destructor del objeto de cuadro de diálogo cuando el objeto queda fuera del ámbito.  
  
 Cuadros de diálogo no modales normalmente se crean y pertenecen a una ventana de vista o el marco primario: ventana de marco principal de la aplicación o una ventana de marco de documento. El valor predeterminado [OnClose](../mfc/reference/cwnd-class.md#onclose) las llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), que destruye la ventana de cuadro de diálogo. Si el cuadro de diálogo permanece independiente, sin punteros o otra semántica de propiedad especial, se debe invalidar [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) para destruir el objeto de cuadro de diálogo de C++. También debe invalidar [OnCancel](../mfc/reference/cdialog-class.md#oncancel) y llamar a `DestroyWindow` desde dentro de él. De lo contrario, el propietario del cuadro de diálogo debería destruir el objeto de C++ cuando ya no es necesario.  
  
## <a name="see-also"></a>Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)


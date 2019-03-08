---
title: Mapping Windows Messages to Your (Clase)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 7e15f52e41d4ac91a839629342258128db86e2d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326678"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapping Windows Messages to Your (Clase)

Si necesita el cuadro de diálogo para controlar los mensajes de Windows, reemplace las funciones de controlador adecuado. Para ello, utilice la ventana Propiedades para [asignar los mensajes de](../mfc/reference/mapping-messages-to-functions.md) a la clase de cuadro de diálogo. Esto escribe una entrada de mapa de mensajes para cada mensaje y agrega las funciones miembro de controlador de mensajes a la clase. Usar el editor de código fuente de Visual C++ para escribir código en los controladores de mensajes.

También puede invalidar las funciones miembro de [CDialog](../mfc/reference/cdialog-class.md) y sus clases base, especialmente [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Controlar y asignar mensajes](../mfc/message-handling-and-mapping.md)

- [Se reemplazan con frecuencia funciones miembro](../mfc/commonly-overridden-member-functions.md)

- [Las funciones miembro se agregan con frecuencia](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

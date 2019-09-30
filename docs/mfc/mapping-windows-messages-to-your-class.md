---
title: Mapping Windows Messages to Your (Clase)
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 0f1207faca56acd709db86478722eba85eeb284a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685607"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapping Windows Messages to Your (Clase)

Si necesita que el cuadro de diálogo controle los mensajes de Windows, invalide las funciones de controlador adecuadas. Para ello, elija la pestaña **vista de clases** en **Explorador de soluciones**, haga clic con el botón derecho en la clase que representa el cuadro de diálogo y elija [Asistente para clases](reference/mfc-class-wizard.md). Use el Asistente para [asignar los mensajes](../mfc/reference/mapping-messages-to-functions.md) a la clase de cuadro de diálogo. De este tipo, se escribe una entrada de mapa de mensajes para cada mensaje y se agregan las funciones miembro del controlador de mensajes a la clase. Utilice el editor de código para escribir código en los controladores de mensajes.

También puede invalidar las funciones miembro de [CDialog](../mfc/reference/cdialog-class.md) y sus clases base, especialmente [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Control y asignación de mensajes](../mfc/message-handling-and-mapping.md)

- [Funciones miembro que se reemplazan normalmente](../mfc/commonly-overridden-member-functions.md)

- [Funciones miembro que se agregan normalmente](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)

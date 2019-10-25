---
title: Cuadros de diálogo modales y no modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 886229a2b66968bf76129ecb1da838bd36e66215
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685189"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Cuadros de diálogo modales y no modales

Puede usar la clase [CDialog](../mfc/reference/cdialog-class.md) para administrar dos tipos de cuadros de diálogo:

- *Cuadros de diálogo modales*, que requieren que el usuario responda antes de continuar con el programa

- *Cuadros de diálogo no modales*, que permanecen en la pantalla y están disponibles para su uso en cualquier momento, pero permiten otras actividades de usuario.

La edición de recursos y los procedimientos para crear una plantilla de cuadro de diálogo son los mismos para los cuadros de diálogo modales y no modales.

La creación de un cuadro de diálogo para el programa requiere los pasos siguientes:

1. Utilice el [Editor de cuadros](../windows/dialog-editor.md) de diálogo para diseñar el cuadro de diálogo y crear su recurso de plantilla de cuadro de diálogo.

1. Cree una clase de cuadro de diálogo.

1. Conecte los [controles del recurso de cuadro de diálogo a los controladores de mensajes](../windows/adding-event-handlers-for-dialog-box-controls.md) en la clase de cuadro de diálogo.

1. Agregue miembros de datos asociados a los controles del cuadro de diálogo y especifique el [intercambio de datos de cuadros](../mfc/dialog-data-exchange.md) de diálogo y las validaciones de datos de [cuadros](../mfc/dialog-data-validation.md) de diálogo para los controles.

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)

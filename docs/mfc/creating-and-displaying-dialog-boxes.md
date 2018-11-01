---
title: Crear y mostrar cuadros de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 778ee0cbb154c65b0cc74a207a175354c2e2a90b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431088"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Crear y mostrar cuadros de diálogo

Creación de un objeto de cuadro de diálogo es una operación en dos fases. Primero, construya el objeto de cuadro de diálogo y después crear la ventana de cuadro de diálogo. Cuadros de diálogo modales y no modales difieren ligeramente en el proceso que se usa para crear y mostrarlos. La tabla siguiente muestra cómo modal y no modal diálogo normalmente se construye y se muestran los cuadros.

### <a name="dialog-creation"></a>Creación del cuadro de diálogo

|Tipo de cuadro de diálogo|Cómo crearla|
|-----------------|----------------------|
|[No modal](../mfc/creating-modeless-dialog-boxes.md)|Construir `CDialog`, a continuación, llame a `Create` función miembro.|
|[Modal](../mfc/creating-modal-dialog-boxes.md)|Construir `CDialog`, a continuación, llame a `DoModal` función miembro.|

Puede crear si lo desea, el cuadro de diálogo desde un [plantilla de cuadro de diálogo en memoria](../mfc/using-a-dialog-template-in-memory.md) que ha construido en lugar de desde un recurso de plantilla de cuadro de diálogo. Esto es un tema avanzado, sin embargo.

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)


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
ms.openlocfilehash: 6d23e4d2c9249ce248eb8092963036f2ba5cacac
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685742"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Crear y mostrar cuadros de diálogo

La creación de un objeto de cuadro de diálogo es una operación en dos fases. En primer lugar, construya el objeto de cuadro de diálogo y, a continuación, cree la ventana de cuadro de diálogo. Los cuadros de diálogo modales y no modales difieren en cierto modo en el proceso que se usa para crearlos y mostrarlos. En la tabla siguiente se muestra cómo se construyen y muestran normalmente los cuadros de diálogo modales y no modales.

### <a name="dialog-creation"></a>Creación de cuadros de diálogo

|Tipo de cuadro de diálogo|Cómo crearlo|
|-----------------|----------------------|
|[No modal](../mfc/creating-modeless-dialog-boxes.md)|Construya `CDialog` y, a continuación, llame a la función miembro `Create`.|
|[DoModal](../mfc/creating-modal-dialog-boxes.md)|Construya `CDialog` y, a continuación, llame a la función miembro `DoModal`.|

Si lo desea, puede crear el cuadro de diálogo a partir de una [plantilla de diálogo en memoria](../mfc/using-a-dialog-template-in-memory.md) que haya creado en lugar de hacerlo desde un recurso de plantilla de cuadro de diálogo. Sin embargo, se trata de un tema avanzado.

## <a name="see-also"></a>Vea también

[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)

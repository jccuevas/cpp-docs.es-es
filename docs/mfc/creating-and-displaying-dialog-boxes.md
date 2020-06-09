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
ms.openlocfilehash: 649d64f8e8b894027b9d6850b62d357d79c1dafa
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616270"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Crear y mostrar cuadros de diálogo

La creación de un objeto de cuadro de diálogo es una operación en dos fases. En primer lugar, construya el objeto de cuadro de diálogo y, a continuación, cree la ventana de cuadro de diálogo. Los cuadros de diálogo modales y no modales difieren en cierto modo en el proceso que se usa para crearlos y mostrarlos. En la tabla siguiente se muestra cómo se construyen y muestran normalmente los cuadros de diálogo modales y no modales.

### <a name="dialog-creation"></a>Creación de cuadros de diálogo

|Tipo de diálogo|Cómo crearlo|
|-----------------|----------------------|
|[Modeless](creating-modeless-dialog-boxes.md)|Construya `CDialog` y después llame a la `Create` función miembro.|
|[DoModal](creating-modal-dialog-boxes.md)|Construya `CDialog` y después llame a la `DoModal` función miembro.|

Si lo desea, puede crear el cuadro de diálogo a partir de una [plantilla de diálogo en memoria](using-a-dialog-template-in-memory.md) que haya creado en lugar de hacerlo desde un recurso de plantilla de cuadro de diálogo. Sin embargo, se trata de un tema avanzado.

## <a name="see-also"></a>Consulte también

[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)

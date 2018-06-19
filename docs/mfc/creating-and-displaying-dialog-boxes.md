---
title: Crear y mostrar cuadros de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fcac345a572f8b33d76692d6852e2dc28698367
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342467"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Crear y mostrar cuadros de diálogo
Crear un objeto de cuadro de diálogo es una operación en dos fases. En primer lugar, construya el objeto de cuadro de diálogo, a continuación, el cuadro de diálogo. Cuadros de diálogo modales y no modales difieren ligeramente en el proceso que se utiliza para crear y mostrarlos. La tabla siguiente muestra el cuadro de diálogo modal y no modal cómo cuadros normalmente se construye y se muestran.  
  
### <a name="dialog-creation"></a>Creación de cuadro de diálogo  
  
|Tipo de cuadro de diálogo|Cómo crearlo|  
|-----------------|----------------------|  
|[No modal](../mfc/creating-modeless-dialog-boxes.md)|Construir `CDialog`, a continuación, llame a **crear** función miembro.|  
|[Modal](../mfc/creating-modal-dialog-boxes.md)|Construir `CDialog`, a continuación, llame a `DoModal` función miembro.|  
  
 Puede crear si lo desea, el cuadro de diálogo desde un [plantilla de cuadro de diálogo en memoria](../mfc/using-a-dialog-template-in-memory.md) que ha construido en lugar de en un recurso de plantilla de cuadro de diálogo. Éste es un tema avanzado, sin embargo.  
  
## <a name="see-also"></a>Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)


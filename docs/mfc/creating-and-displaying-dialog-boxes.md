---
title: "Crear y mostrar cuadros de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 109c4f2e8272293ccfcb58924380c586f8078536
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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


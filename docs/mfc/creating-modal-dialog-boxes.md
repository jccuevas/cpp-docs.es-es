---
title: Crear cuadros de diálogo modales | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a8bc947dbaf9cecc680f3cdbd8e6b429d2bcd5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-modal-dialog-boxes"></a>Crear cuadros de diálogo modales
Para crear un cuadro de diálogo modal, llame a cualquiera de los dos constructores públicos declarados en [CDialog](../mfc/reference/cdialog-class.md). A continuación, llamar al objeto de cuadro de diálogo [DoModal](../mfc/reference/cdialog-class.md#domodal) función de miembro para mostrar el cuadro de diálogo y administrar la interacción con él hasta que el usuario elija Aceptar o Cancelar. Esta administración por `DoModal` es lo que hace que el cuadro de diálogo modal. Para los cuadros de diálogo modales, `DoModal` carga el recurso de cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)


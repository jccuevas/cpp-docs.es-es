---
title: Cuadros de diálogo modales y no modales | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4f03d67e1eb9962f4303694db4850e800151404
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="modal-and-modeless-dialog-boxes"></a>Cuadros de diálogo modales y no modales
Puede utilizar la clase [CDialog](../mfc/reference/cdialog-class.md) para administrar dos tipos de cuadros de diálogo:  
  
-   *Cuadros de diálogo modales*, que requiere que el usuario responda antes de continuar con el programa  
  
-   *Cuadros de diálogo no modales*, lo que permanezca en la pantalla y están disponible para su uso en cualquier momento, pero permitir que otras actividades de usuario  
  
 La edición de recursos y los procedimientos para crear una plantilla de cuadro de diálogo son los mismos para cuadros de diálogo modales y no modales.  
  
 Crear un cuadro de diálogo para el programa requiere los pasos siguientes:  
  
1.  Use la [editor de cuadro de diálogo](../windows/dialog-editor.md) para diseñar el cuadro de diálogo y crear el recurso de plantilla de cuadro de diálogo.  
  
2.  Cree una clase de cuadro de diálogo.  
  
3.  Conectar el [controles del recurso de cuadro de diálogo para controladores de mensajes](../windows/adding-event-handlers-for-dialog-box-controls.md) en la clase de cuadro de diálogo.  
  
4.  Agregar miembros de datos asociada a los controles del cuadro de diálogo y para especificar [intercambio de datos de cuadros de diálogo](../mfc/dialog-data-exchange.md) y [validaciones de datos de cuadro de diálogo](../mfc/dialog-data-validation.md) para los controles.  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)


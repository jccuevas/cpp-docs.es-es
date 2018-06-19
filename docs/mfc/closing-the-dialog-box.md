---
title: Cierre el cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c800c204fd09057585064397d459f92c9ded272d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341750"
---
# <a name="closing-the-dialog-box"></a>Cerrar el cuadro de diálogo
Cuadro de diálogo modal se cierra cuando el usuario elige uno de sus botones, normalmente el botón Aceptar o el botón Cancelar. Si se elige el botón Aceptar o cancelar, Windows enviar el objeto de cuadro de diálogo una **BN_CLICKED** mensaje de notificación de controles con el botón del identificador, ya sea **IDOK** o **IDCANCEL**. `CDialog` proporciona funciones controladoras predeterminadas para estos mensajes: `OnOK` y `OnCancel`. La llamada de controladores de forma predeterminada el `EndDialog` función de miembro para cerrar el cuadro de diálogo. También puede llamar a `EndDialog` desde su propio código. Para obtener más información, consulte el [EndDialog](../mfc/reference/cdialog-class.md#enddialog) función miembro de clase `CDialog` en el *referencia de MFC*.  
  
 Para organizar para cerrar y eliminar un cuadro de diálogo no modal, invalidar `PostNcDestroy` e invocar el **eliminar** operador en el **esto** puntero. [Destruir el cuadro de diálogo](../mfc/destroying-the-dialog-box.md) explica qué ocurre después.  
  
## <a name="see-also"></a>Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)


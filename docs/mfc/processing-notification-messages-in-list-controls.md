---
title: Procesar mensajes de notificación en controles de lista | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5412bbf1fcb7e139394b9563965244080e5c179
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932086"
---
# <a name="processing-notification-messages-in-list-controls"></a>Procesar mensajes de notificación en los controles de lista
Como los usuarios haga clic en los encabezados de columna, arrastre los iconos, edite las etiquetas y así sucesivamente, el control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) envía mensajes de notificación a su ventana primaria. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario hace clic en un encabezado de columna, puede ordenar los elementos basados en el contenido de la columna seleccionada, como en Microsoft Outlook.  
  
 Procese los mensajes WM_NOTIFY desde el control de lista en la clase de vista o cuadro de diálogo. Utilice la ventana Propiedades para crear un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) función de controlador con una instrucción switch en función de qué mensaje de notificación se está controlando.  
  
 Para obtener una lista de las notificaciones que puede enviar un control de lista a su ventana primaria, vea [referencia de Control de vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774737) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)


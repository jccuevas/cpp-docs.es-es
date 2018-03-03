---
title: "Procesar mensajes de notificación de Control de pestaña | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 840ff6fc5dd47a2059e62608b5a5d6f231f8f17c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="processing-tab-control-notification-messages"></a>Procesar los mensajes de notificación del control de pestaña
Como los usuarios, haga clic en las fichas o botones, el control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) envía mensajes de notificación a su ventana primaria. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario hace clic en una pestaña, puede que desee preestablecer datos de control en la página antes de mostrarlo.  
  
 Proceso **WM_NOTIFY** mensajes desde el control de ficha en la clase de vista o cuadro de diálogo. Utilice la ventana Propiedades para crear un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) función de controlador con una instrucción switch en función de qué mensaje de notificación se está controlando. Para obtener una lista de las notificaciones que puede enviar un control de fichas a su ventana primaria, vea la **notificaciones** sección de [referencia de Control de pestaña](http://msdn.microsoft.com/library/windows/desktop/bb760548) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)


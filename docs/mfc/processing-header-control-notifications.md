---
title: Procesar notificaciones del Control de encabezado | Documentos de Microsoft
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
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a442e6aadf7c91918cd523c29330e79c753b115c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="processing-header-control-notifications"></a>Procesar notificaciones del control de encabezado
En la clase de vista o cuadro de diálogo, utilice la ventana Propiedades para crear un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) función de controlador con una instrucción switch para cualquier control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) mensajes de notificación que desee controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). Las notificaciones se envían a la ventana primaria cuando el usuario hace clic o doble clic en un elemento de encabezado, arrastra un divisor entre elementos y así sucesivamente.  
  
 Los mensajes de notificación asociados a un control de encabezado se enumeran en [referencia de Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775239) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)


---
title: Procesar notificaciones del Control de encabezado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a0fe657089c33679cf8d18f95268a70335804c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="processing-header-control-notifications"></a>Procesar notificaciones del control de encabezado
En la clase de vista o cuadro de diálogo, utilice la ventana Propiedades para crear un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) función de controlador con una instrucción switch para cualquier control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) mensajes de notificación que desee controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). Las notificaciones se envían a la ventana primaria cuando el usuario hace clic o doble clic en un elemento de encabezado, arrastra un divisor entre elementos y así sucesivamente.  
  
 Los mensajes de notificación asociados a un control de encabezado se enumeran en [referencia de Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775239) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)


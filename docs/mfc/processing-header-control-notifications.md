---
title: Procesar notificaciones del Control de encabezado | Microsoft Docs
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
ms.openlocfilehash: 539e7411dcc47be17bb10a5322e30a524679ca8c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194216"
---
# <a name="processing-header-control-notifications"></a>Procesar notificaciones del control de encabezado
En la clase de vista o cuadro de diálogo, utilice la ventana Propiedades para crear un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) función de controlador con una instrucción switch para cualquier control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) mensajes de notificación que desee controlar (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). Las notificaciones se envían a la ventana primaria cuando el usuario hace clic o hace doble clic en un elemento de encabezado, arrastra un divisor entre elementos y así sucesivamente.  
  
 Los mensajes de notificación asociados con un control de encabezado se enumeran en [referencia de Control de encabezado](https://msdn.microsoft.com/library/windows/desktop/bb775239) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)


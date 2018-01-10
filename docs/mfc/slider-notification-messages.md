---
title: "Mensajes de notificación de control deslizante | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a4fc9e9065017e04b6375d1e5a8e336d4366755
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="slider-notification-messages"></a>Mensajes de notificación de control deslizante
Un control deslizante notifica a su ventana primaria de las acciones del usuario mediante el envío de primario `WM_HSCROLL` o `WM_VSCROLL` mensajes, dependiendo de la orientación del control deslizante. Para controlar estos mensajes, agregar controladores para la `WM_HSCROLL` y `WM_VSCROLL` mensajes a la ventana primaria. El [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) y [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) un código de notificación, la posición del control deslizante y un puntero a funciones miembro que se le pasará la [CSliderCtrl](../mfc/reference/csliderctrl-class.md) objeto. Tenga en cuenta que el puntero es de tipo **CScrollBar \***  aunque hace referencia a un `CSliderCtrl` objeto. Debe convertir el tipo de este puntero si es necesario manipular el control deslizante.  
  
 En lugar de usar la barra códigos de notificación de desplazamiento, controles deslizantes envían un conjunto distinto de códigos de notificación. Un control deslizante envía el **TB_BOTTOM**, **TB_LINEDOWN**, **TB_LINEUP**, y **TB_TOP** códigos de notificación solo cuando el usuario interactúa con un control deslizante mediante el teclado. El **TB_THUMBPOSITION** y **TB_THUMBTRACK** solo se envían mensajes de notificación cuando el usuario está utilizando el mouse. El **TB_ENDTRACK**, **TB_PAGEDOWN**, y **TB_PAGEUP** códigos de notificación se envían en ambos casos.  
  
 En la tabla siguiente se enumera los mensajes de notificación del control deslizante y los eventos (códigos de tecla virtuales o los eventos del mouse) que provocan el envío de notificaciones. (Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h.)  
  
|Mensaje de notificación|Evento que provoca que se envíe notificación|  
|--------------------------|-------------------------------------------|  
|**TB_BOTTOM**|**VK_END**|  
|**TB_ENDTRACK**|`WM_KEYUP`(el usuario suelta una tecla que envía un código de tecla virtual relevante)|  
|**TB_LINEDOWN**|**VK_RIGHT** o **VK_DOWN**|  
|**TB_LINEUP**|**VK_LEFT** o **VK_UP**|  
|**TB_PAGEDOWN**|**VK_NEXT** (el usuario hace clic en el canal debajo o a la derecha del control deslizante)|  
|**TB_PAGEUP**|**VK_PRIOR** (el usuario hace clic en el canal encima o a la izquierda del control deslizante)|  
|**TB_THUMBPOSITION**|`WM_LBUTTONUP`Después de un **TB_THUMBTRACK** mensaje de notificación|  
|**TB_THUMBTRACK**|Movimiento del control deslizante (el usuario arrastra el control deslizante)|  
|**TB_TOP**|**VK_HOME**|  
  
## <a name="see-also"></a>Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)


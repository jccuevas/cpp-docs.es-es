---
title: Mensajes de notificación de control deslizante | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c383458905d16dda935254e56a5aa9f56a153e83
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956166"
---
# <a name="slider-notification-messages"></a>Mensajes de notificación de control deslizante
Un control deslizante notifica a su ventana primaria de las acciones del usuario mediante el envío de mensajes WM_HSCROLL o WM_VSCROLL, dependiendo de la orientación del control deslizante del elemento primario. Para controlar estos mensajes, agregue controladores para los mensajes WM_HSCROLL y WM_VSCROLL mensajes a la ventana primaria. El [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) y [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) un código de notificación, la posición del control deslizante y un puntero a funciones miembro que se le pasará la [CSliderCtrl](../mfc/reference/csliderctrl-class.md) objeto. Tenga en cuenta que el puntero es de tipo `CScrollBar *` aunque hace referencia a un `CSliderCtrl` objeto. Debe convertir el tipo de este puntero si es necesario manipular el control deslizante.  
  
 En lugar de usar la barra códigos de notificación de desplazamiento, controles deslizantes envían un conjunto distinto de códigos de notificación. Un control deslizante envía los códigos de notificación TB_BOTTOM, TB_LINEDOWN, TB_LINEUP y TB_TOP sólo cuando el usuario interactúa con un control deslizante mediante el teclado. Los mensajes de notificación TB_THUMBPOSITION y TB_THUMBTRACK sólo se envían cuando el usuario está utilizando el mouse. Los códigos de notificación TB_ENDTRACK, TB_PAGEDOWN y TB_PAGEUP se envían en ambos casos.  
  
 En la tabla siguiente se enumera los mensajes de notificación del control deslizante y los eventos (códigos de tecla virtuales o los eventos del mouse) que provocan el envío de notificaciones. (Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h.)  
  
|Mensaje de notificación|Evento que provoca que se envíe notificación|  
|--------------------------|-------------------------------------------|  
|TB_BOTTOM|VK_END|  
|TB_ENDTRACK|WM_KEYUP (el usuario suelta una tecla que envía un código de tecla virtual relevante)|  
|TB_LINEDOWN|VK_RIGHT o VK_DOWN|  
|TB_LINEUP|VK_LEFT o VK_UP|  
|TB_PAGEDOWN|VK_NEXT (el usuario hace clic en el canal debajo o a la derecha del control deslizante)|  
|TB_PAGEUP|VK_PRIOR (el usuario hace clic en el canal encima o a la izquierda del control deslizante)|  
|TB_THUMBPOSITION|WM_LBUTTONUP a continuación un mensaje de notificación TB_THUMBTRACK|  
|TB_THUMBTRACK|Movimiento del control deslizante (el usuario arrastra el control deslizante)|  
|TB_TOP|VK_HOME|  
  
## <a name="see-also"></a>Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)


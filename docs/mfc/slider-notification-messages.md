---
title: "Mensajes de notificaci&#243;n de control deslizante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSliderCtrl (clase), notificaciones"
  - "mensajes, notificación"
  - "notificaciones, CSliderCtrl"
  - "controles deslizantes, mensajes de notificación"
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Mensajes de notificaci&#243;n de control deslizante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control deslizante notifica a su ventana primaria de las acciones del usuario enviándole `WM_HSCROLL` o mensajes principales de `WM_VSCROLL` , dependiendo de la orientación del control deslizante.  Para administrar estos mensajes, agregue controladores para los mensajes de `WM_HSCROLL` y de `WM_VSCROLL` a la ventana primaria.  Las funciones miembro de [OnHScroll](../Topic/CWnd::OnHScroll.md) y de [OnVScroll](../Topic/CWnd::OnVScroll.md) se pasa un código de notificación, la posición del control deslizante, y un puntero al objeto de [CSliderCtrl](../mfc/reference/csliderctrl-class.md) .  Observe que el puntero es de **CScrollBar \*** tipo aunque elija `CSliderCtrl` un objeto.  Puede ser necesario convertir este puntero si necesita manipular el control deslizante.  
  
 En lugar de utilizar los códigos de notificación de la barra de desplazamiento, los controles deslizantes envían un conjunto diferente de códigos de notificación.  Un control deslizante envía los códigos de notificación de **TB\_BOTTOM**, de **TB\_LINEDOWN**, de **TB\_LINEUP**, y de **TB\_TOP** sólo cuando el usuario interactúa con un control deslizante mediante el teclado.  Los mensajes de notificación de **TB\_THUMBPOSITION** y de **TB\_THUMBTRACK** se envían únicamente cuando el usuario está utilizando el mouse.  Los códigos de notificación de **TB\_ENDTRACK**, de **TB\_PAGEDOWN**, y de **TB\_PAGEUP** se envían en ambos casos.  
  
 La tabla siguiente se muestran los mensajes de notificación de control slider y eventos \(los códigos de tecla virtual o eventos del mouse\) que causa notificaciones de ser enviados. \(Para obtener una lista de códigos de tecla virtual estándar, vea Winuser.h.\)  
  
|Mensaje de notificación|Evento que produce la notificación se envía|  
|-----------------------------|-------------------------------------------------|  
|**TB\_BOTTOM**|**VK\_END**|  
|**TB\_ENDTRACK**|`WM_KEYUP` \(el usuario lanzó una clave que envió un código de tecla virtual pertinente\)|  
|**TB\_LINEDOWN**|**VK\_RIGHT** o **VK\_DOWN**|  
|**TB\_LINEUP**|**VK\_LEFT** o **VK\_UP**|  
|**TB\_PAGEDOWN**|**VK\_NEXT** \(el usuario hizo clic en el canal debajo o a la derecha del control deslizante\)|  
|**TB\_PAGEUP**|**VK\_PRIOR** \(el usuario hizo clic en el canal sobre o a la izquierda del control deslizante\)|  
|**TB\_THUMBPOSITION**|`WM_LBUTTONUP` después de un mensaje de notificación de **TB\_THUMBTRACK**|  
|**TB\_THUMBTRACK**|Mover el control deslizante \(el usuario arrastró el control deslizante\)|  
|**TB\_TOP**|**VK\_HOME**|  
  
## Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)
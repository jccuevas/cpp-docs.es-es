---
title: Controlar la notificación TTN_NEEDTEXT para la información sobre herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ddfe6660854ae4cbdba2398aa4102fd612d17ddc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114584"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Controlar la notificación TTN_NEEDTEXT para la información sobre herramientas
Como parte de [habilitar información sobre herramientas](../mfc/enabling-tool-tips.md), controla la **TTN_NEEDTEXT** mensaje agregando la siguiente entrada al mapa de mensajes de la ventana propietaria:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
*memberFxn*<br/>
La función miembro se llama cuando es necesario el texto para este botón.  
  
 Tenga en cuenta que el identificador de una información sobre herramientas es siempre 0.  
  
 Declare la función controladora en la definición de clase como sigue:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 donde los parámetros en cursiva son:  
  
*identificador*<br/>
Identificador del control que envía la notificación. No usado. El identificador del control se toma de la **NMHDR** estructura.  
  
*pNMHDR*<br/>
Un puntero a la [estructura NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa) estructura. Esta estructura también se explica con más detalle en [TOOLTIPTEXT (estructura)](../mfc/tooltiptext-structure.md).  
  
*pResult*<br/>
Un puntero al código de resultado se puede establecer antes de volver. **TTN_NEEDTEXT** controladores pueden omitir el *pResult* parámetro.  
  
 Como ejemplo de un controlador de vista de formulario de notificación:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 Llame a `EnableToolTips` (este fragmento que se toman de `OnInitDialog`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Información sobre herramientas en ventanas no derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)


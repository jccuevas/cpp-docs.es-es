---
title: Controlar la notificación TTN_NEEDTEXT para la información sobre herramientas
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 75850dbf92587cf654d4f7a39ea54af1fd9dd5bd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620079"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>Controlar la notificación TTN_NEEDTEXT para la información sobre herramientas

Como parte de la [habilitación de la información sobre herramientas](enabling-tool-tips.md), puede controlar el mensaje de **TTN_NEEDTEXT** agregando la siguiente entrada al mapa de mensajes de la ventana propietaria:

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
Función miembro a la que se va a llamar cuando se necesite texto para este botón.

Tenga en cuenta que el identificador de una información sobre herramientas es siempre 0.

Declare la función de controlador en la definición de clase de la siguiente manera:

[!code-cpp[NVC_MFCControlLadenDialog#53](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

donde los parámetros en cursiva son:

*id*<br/>
Identificador del control que envió la notificación. No se usa. El identificador de control se toma de la estructura **NMHDR** .

*pNMHDR*<br/>
Puntero a la estructura [NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) . Esta estructura también se describe con más detalle en [la estructura ToolTipText](tooltiptext-structure.md).

*pResult*<br/>
Un puntero a código de resultado que se puede establecer antes de devolver. Los controladores de **TTN_NEEDTEXT** pueden omitir el parámetro *pResult* .

Como ejemplo de un controlador de notificación de vista de formulario:

[!code-cpp[NVC_MFCControlLadenDialog#54](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Llame a `EnableToolTips` (este fragmento procede de `OnInitDialog` ):

[!code-cpp[NVC_MFCControlLadenDialog#55](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Consulte también

[Información sobre herramientas en ventanas no derivadas de CFrameWnd](tool-tips-in-windows-not-derived-from-cframewnd.md)

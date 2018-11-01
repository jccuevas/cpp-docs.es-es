---
title: Controlar las notificaciones de información sobre herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 973c4a12f3b3bdc91269736874b7193130290a76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548920"
---
# <a name="handling-tool-tip-notifications"></a>Controlar las notificaciones de información sobre herramientas

Al especificar el **TBSTYLE_TOOLTIPS** estilo, la barra de herramientas crea y administra un control. Una información sobre herramientas es una pequeña ventana emergente que contiene una línea de texto que describe un botón de barra de herramientas. La información sobre herramientas está oculta, que aparecen solo cuando el usuario coloca el cursor sobre un botón de barra de herramientas y deja allí durante aproximadamente medio segundo. La información sobre herramientas se muestra junto al cursor.

Antes de que se muestra la información sobre herramientas, el **TTN_NEEDTEXT** mensaje de notificación se envía a la ventana propietaria de la barra de herramientas para recuperar el texto descriptivo para el botón. Si la ventana propietaria de la barra de herramientas es una `CFrameWnd` ventana, la herramienta de sugerencias se muestran sin ningún esfuerzo adicional, porque `CFrameWnd` tiene un controlador predeterminado para el **TTN_NEEDTEXT** notificación. Si la ventana propietaria de la barra de herramientas no se derive de `CFrameWnd`, por ejemplo, una vista de formulario o de cuadro de diálogo, debe agregar una entrada al mapa de mensajes de la ventana propietaria y proporcionar un controlador de notificación en el mapa de mensajes. La entrada al mapa de mensajes de la ventana propietaria es como sigue:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>Comentarios

*memberFxn*<br/>
La función miembro se llama cuando es necesario el texto para este botón.

Tenga en cuenta que el identificador de una información sobre herramientas es siempre 0.

Además el **TTN_NEEDTEXT** notificación, un control puede enviar las siguientes notificaciones a un control de barra de herramientas:

|notificación|Significado|
|------------------|-------------|
|**TTN_NEEDTEXTA**|Control de información sobre herramientas requiere texto ASCII (sólo en Windows 95)|
|**TTN_NEEDTEXTW**|Control de información sobre herramientas requiere texto UNICODE (solo Windows NT)|
|**TBN_HOTITEMCHANGE**|Indica que el elemento activo (resaltado) ha cambiado.|
|**NM_RCLICK**|Indica que el usuario ha hecho un botón.|
|**TBN_DRAGOUT**|Indica que el usuario ha hecho clic con el botón y arrastrando el puntero del botón. Permite que una aplicación implementar arrastrar y colocar desde un botón de barra de herramientas. Cuando se recibe esta notificación, la aplicación comenzará la operación de arrastrar y colocar la operación.|
|**TBN_DROPDOWN**|Indica que el usuario haya hecho clic en un botón que usa el **TBSTYLE_DROPDOWN** estilo.|
|**TBN_GETOBJECT**|Indica que el usuario mueve el puntero sobre un botón que usa el **TBSTYLE_DROPPABLE** estilo.|

Para una función de controlador de ejemplo y obtener más información acerca de cómo habilitar información sobre herramientas, vea [información sobre herramientas](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

## <a name="see-also"></a>Vea también

[Uso de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)


---
title: Controlar las notificaciones de información sobre herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 41e3dbfc2269f5fbf3c12dc00c19f8a2253fd16a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626440"
---
# <a name="handling-tool-tip-notifications"></a>Controlar las notificaciones de información sobre herramientas

Al especificar el estilo de **TBSTYLE_TOOLTIPS** , la barra de herramientas crea y administra un control de información sobre herramientas. Una información sobre herramientas es una pequeña ventana emergente que contiene una línea de texto que describe un botón de la barra de herramientas. La información sobre herramientas está oculta, solo aparece cuando el usuario coloca el cursor en un botón de la barra de herramientas y lo deja allí durante aproximadamente un segundo medio. La información sobre herramientas se muestra cerca del cursor.

Antes de que se muestre la información sobre herramientas, el mensaje de notificación de **TTN_NEEDTEXT** se envía a la ventana propietaria de la barra de herramientas para recuperar el texto descriptivo para el botón. Si la ventana propietaria de la barra de herramientas es una `CFrameWnd` ventana, la información sobre herramientas se muestra sin ningún esfuerzo adicional, ya `CFrameWnd` que tiene un controlador predeterminado para la notificación **TTN_NEEDTEXT** . Si la ventana propietaria de la barra de herramientas no se deriva de `CFrameWnd` , como un cuadro de diálogo o una vista de formulario, debe agregar una entrada al mapa de mensajes de la ventana propietaria y proporcionar un controlador de notificación en el mapa de mensajes. La entrada del mapa de mensajes de la ventana propietaria es la siguiente:

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>Observaciones

*memberFxn*<br/>
Función miembro a la que se va a llamar cuando se necesite texto para este botón.

Tenga en cuenta que el identificador de una información sobre herramientas es siempre 0.

Además de la notificación de **TTN_NEEDTEXT** , un control de información sobre herramientas puede enviar las siguientes notificaciones a un control de barra de herramientas:

|Notificación|Significado|
|------------------|-------------|
|**TTN_NEEDTEXTA**|El control de información sobre herramientas requiere texto ASCII (solo Windows 95)|
|**TTN_NEEDTEXTW**|El control de información sobre herramientas requiere texto Unicode (solo Windows NT)|
|**TBN_HOTITEMCHANGE**|Indica que ha cambiado el elemento activo (resaltado).|
|**NM_RCLICK**|Indica que el usuario hizo clic con el botón secundario en un botón.|
|**TBN_DRAGOUT**|Indica que el usuario hizo clic en el botón y arrastró el puntero fuera del botón. Permite a una aplicación implementar la función de arrastrar y colocar desde un botón de la barra de herramientas. Al recibir esta notificación, la aplicación iniciará la operación de arrastrar y colocar.|
|**TBN_DROPDOWN**|Indica que el usuario ha haga clic en un botón que usa el estilo **TBSTYLE_DROPDOWN** .|
|**TBN_GETOBJECT**|Indica que el usuario ha despasado el puntero sobre un botón que usa el estilo **TBSTYLE_DROPPABLE** .|

Para obtener una función de controlador de ejemplo y obtener más información sobre cómo habilitar la información sobre herramientas, vea [información sobre herramientas](tool-tips-in-windows-not-derived-from-cframewnd.md).

## <a name="see-also"></a>Consulte también

[Usar CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Permite](controls-mfc.md)

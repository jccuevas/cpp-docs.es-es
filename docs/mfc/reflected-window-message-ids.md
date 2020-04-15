---
title: Identificadores de mensaje de ventana reflejada
ms.date: 11/04/2016
f1_keywords:
- OCM_CTLCOLORBTN
- OCM_PARENTNOTIFY
- OCM_VKEYTOITEM
- OCM_CTLCOLORSTATIC
- OCM_HSCROLL
- OCM_CHARTOITEM
- OCM_DRAWITEM
- OCM_MEASUREITEM
- OCM_COMPAREITEM
- OCM_COMMAND
- OCM_NOTIFY
- OCM_CTLCOLORMSGBOX
- OCM_DELETEITEM
- OCM_CTLCOLORLISTBOX
- OCM_CTLCOLORDLG
- OCM_CTLCOLOREDIT
- OCM_CTLCOLORSCROLLBAR
- OCM_VSCROLL
- OCM_CTLCOLOR
helpviewer_keywords:
- OCM_HSCROLL message [MFC]
- OCM_PARENTNOTIFY message [MFC]
- messages, reflected
- reflected messages, window message Ids
- OCM_CTLCOLORDLG message [MFC]
- OCM_COMMAND message [MFC]
- OCM_CTLCOLORMSGBOX message [MFC]
- OCM_COMPAREITEM message [MFC]
- OCM_DRAWITEM message [MFC]
- OCM_VSCROLL message [MFC]
- OCM_CTLCOLOREDIT message [MFC]
- OCM_VKEYTOITEM message [MFC]
- OCM_CHARTOITEM message [MFC]
- OCM_CTLCOLORBTN message [MFC]
- OCM_CTLCOLORSTATIC message [MFC]
- OCM_MEASUREITEM message [MFC]
- OCM_CTLCOLOR message [MFC]
- OCM_CTLCOLORSCROLLBAR message [MFC]
- OCM_ messages
- OCM_DELETEITEM message [MFC]
- OCM_CTLCOLORLISTBOX message [MFC]
- OCM_NOTIFY message [MFC]
- reflected messages
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
ms.openlocfilehash: 5b44a1b4e96d92d9ddd150a5b5f68cf83863f8db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372851"
---
# <a name="reflected-window-message-ids"></a>Identificadores de mensaje de ventana reflejada

Una forma rápida de crear un control ActiveX u otro control especializado es subclase una ventana. Para obtener más información, vea [Controles ActiveX de MFC: Subclase de un control de Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

Para evitar que el contenedor del control reciba los mensajes de ventana enviados por un control de Windows subclase, [COleControl](../mfc/reference/colecontrol-class.md) crea una ventana "reflector" para interceptar determinados mensajes de ventana y enviarlos de vuelta al control. El control, en su procedimiento de ventana, puede procesar estos mensajes reflejados realizando las acciones adecuadas para un control ActiveX.

En la tabla siguiente se muestran los mensajes que se interceptan y los mensajes correspondientes que envía la ventana del reflector.

|Mensaje enviado por el control|Mensaje reflejado en el control|
|---------------------------------|--------------------------------------|
|[WM_COMMAND](/windows/win32/menurc/wm-command)|OCM_COMMAND|
|[WM_CTLCOLORBTN](/windows/win32/Controls/wm-ctlcolorbtn)|OCM_CTLCOLORBTN|
|[WM_CTLCOLOREDIT](/windows/win32/Controls/wm-ctlcoloredit)|OCM_CTLCOLOREDIT|
|[WM_CTLCOLORDLG](/windows/win32/dlgbox/wm-ctlcolordlg)|OCM_CTLCOLORDLG|
|[WM_CTLCOLORLISTBOX](/windows/win32/Controls/wm-ctlcolorlistbox)|OCM_CTLCOLORLISTBOX|
|[WM_CTLCOLORSCROLLBAR](/windows/win32/Controls/wm-ctlcolorscrollbar)|OCM_CTLCOLORSCROLLBAR|
|[WM_CTLCOLORSTATIC](/windows/win32/Controls/wm-ctlcolorstatic)|OCM_CTLCOLORSTATIC|
|[WM_DRAWITEM](/windows/win32/Controls/wm-drawitem)|OCM_DRAWITEM|
|[WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem)|OCM_MEASUREITEM|
|[WM_DELETEITEM](/windows/win32/Controls/wm-deleteitem)|OCM_DELETEITEM|
|[WM_VKEYTOITEM](/windows/win32/Controls/wm-vkeytoitem)|OCM_VKEYTOITEM|
|[WM_CHARTOITEM](/windows/win32/Controls/wm-chartoitem)|OCM_CHARTOITEM|
|[WM_COMPAREITEM](/windows/win32/Controls/wm-compareitem)|OCM_COMPAREITEM|
|[WM_HSCROLL](/windows/win32/Controls/wm-hscroll)|OCM_HSCROLL|
|[WM_VSCROLL](/windows/win32/Controls/wm-vscroll)|OCM_VSCROLL|
|[WM_PARENTNOTIFY](/previous-versions/windows/desktop/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY|
|[WM_NOTIFY](/windows/win32/controls/wm-notify)|OCM_NOTIFY|

> [!NOTE]
> Si el control se ejecuta en un sistema Win32, hay varios tipos de mensajes de WM_CTLCOLOR\* que puede recibir. Para obtener más información, consulte WM_CTLCOLORBTN, WM_CTLCOLORDLG, WM_CTLCOLOREDIT, WM_CTLCOLORLISTBOX, WM_CTLCOLORMSGBOX, WM_CTLCOLORSCROLLBAR, WM_CTLCOLORSTATIC.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC: Creación de subclases de un control de Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)<br/>
[TN062: Reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md)

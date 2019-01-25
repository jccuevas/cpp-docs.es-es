---
title: Teclas de acceso rápido específicas del subproceso
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 68c50ec5f29dab271f9af9abc50eb72ec15157e7
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893332"
---
# <a name="thread-specific-hot-keys"></a>Teclas de acceso rápido específicas del subproceso

Una aplicación establece una tecla de acceso rápido específicas del subproceso ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) mediante el uso de la Windows `RegisterHotKey` función. Cuando el usuario presiona una tecla de acceso rápido específicas del subproceso, Windows envía una [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) mensaje al principio de la cola de mensajes de un subproceso determinado. El mensaje WM_HOTKEY contiene el código de tecla virtual, el estado de desplazamiento y el identificador definido por el usuario de la tecla de acceso rápido específica que se presionó. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h. Para obtener más información sobre este método, consulte [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

Tenga en cuenta que marca el estado de desplazamiento usado en la llamada a `RegisterHotKey` no son los mismos que los devueltos por la [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) función miembro; tendrá que traducir estos indicadores antes de llamar a `RegisterHotKey`.

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)


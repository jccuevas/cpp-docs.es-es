---
title: Teclas de acceso rápido específicas del subproceso
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 49bac6ac357924c26f131bbd8e1092cd74514167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511139"
---
# <a name="thread-specific-hot-keys"></a>Teclas de acceso rápido específicas del subproceso

Una aplicación establece una tecla de acceso rápido específica del subproceso ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) mediante `RegisterHotKey` la función de Windows. Cuando el usuario presiona una tecla de acceso rápido específica del subproceso, Windows envía un mensaje [WM_HOTKEY](/windows/win32/inputdev/wm-hotkey) al principio de la cola de mensajes de un subproceso determinado. El mensaje WM_HOTKEY contiene el código de tecla virtual, el estado de desplazamiento y el identificador definido por el usuario de la tecla de acceso rápido específica que se presionó. Para obtener una lista de códigos de tecla virtual estándar, vea Winuser. h. Para obtener más información sobre este método, vea [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

Tenga en cuenta que las marcas de estado de desplazamiento utilizadas `RegisterHotKey` en la llamada a no son las mismas que las devueltas por la función miembro [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) ; tendrá que traducir `RegisterHotKey`estas marcas antes de llamar a.

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

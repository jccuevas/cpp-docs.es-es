---
title: Teclas de acceso directo globales
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 59918648ea24fd1e2a86ca786de3081cd6cca2df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508561"
---
# <a name="global-hot-keys"></a>Teclas de acceso directo globales

Una tecla de acceso rápido global está asociada a una ventana no secundaria determinada. Permite al usuario activar la ventana desde cualquier parte del sistema. Una aplicación establece una tecla de acceso rápido global para una ventana determinada mediante el envío del mensaje [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) a esa ventana. Por ejemplo, si `m_HotKeyCtrl` es el objeto [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) y `pMainWnd` es un puntero a la ventana que se va a activar cuando se presiona la tecla de acceso rápido, podría usar el código siguiente para asociar la tecla de acceso rápido especificada en el control con la ventana señalada por `pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

Siempre que el usuario presiona una tecla de acceso rápido global, la ventana especificada recibe un mensaje [WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand) que especifica **SC_HOTKEY** como el tipo del comando. Este mensaje también activa la ventana que lo recibe. Dado que este mensaje no incluye información sobre la tecla exacta que se presionó, el uso de este método no permite distinguir entre las diferentes teclas de acceso rápido que se pueden adjuntar a la misma ventana. La tecla de acceso rápido sigue siendo válida hasta que se cierre la aplicación que envió **WM_SETHOTKEY** .

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

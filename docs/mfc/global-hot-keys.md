---
title: Teclas de acceso directo globales
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 5fdcfbef1db0d20126f8eac144f74f8b92410504
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618734"
---
# <a name="global-hot-keys"></a>Teclas de acceso directo globales

Una tecla de acceso rápido global está asociada a una ventana no secundaria determinada. Permite al usuario activar la ventana desde cualquier parte del sistema. Una aplicación establece una tecla de acceso rápido global para una ventana determinada mediante el envío del mensaje de [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) a esa ventana. Por ejemplo, si `m_HotKeyCtrl` es el objeto [CHotKeyCtrl](reference/chotkeyctrl-class.md) y `pMainWnd` es un puntero a la ventana que se va a activar cuando se presiona la tecla de acceso rápido, podría usar el código siguiente para asociar la tecla de acceso rápido especificada en el control con la ventana a la que señala `pMainWnd` .

[!code-cpp[NVC_MFCControlLadenDialog#18](codesnippet/cpp/global-hot-keys_1.cpp)]

Siempre que el usuario presiona una tecla de acceso rápido global, la ventana especificada recibe un mensaje [WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand) que especifica **SC_HOTKEY** como el tipo del comando. Este mensaje también activa la ventana que lo recibe. Dado que este mensaje no incluye información sobre la tecla exacta que se presionó, el uso de este método no permite distinguir entre las diferentes teclas de acceso rápido que se pueden adjuntar a la misma ventana. La tecla de acceso rápido sigue siendo válida hasta que se cierre la aplicación que envió **WM_SETHOTKEY** .

## <a name="see-also"></a>Consulte también

[Uso de CHotKeyCtrl](using-chotkeyctrl.md)<br/>
[Permite](controls-mfc.md)

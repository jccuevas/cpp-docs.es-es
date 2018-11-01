---
title: Teclas de acceso directo globales
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 4cafee311f71d8165380b3fb7e192e7032b7941c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529940"
---
# <a name="global-hot-keys"></a>Teclas de acceso directo globales

Tecla de acceso rápido global está asociada con una ventana no secundaria específica. Permite al usuario activar la ventana desde cualquier parte del sistema. Una aplicación establece una tecla de acceso rápido global para una ventana concreta mediante el envío de la [mensaje WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) mensaje a esa ventana. Por ejemplo, si `m_HotKeyCtrl` es el [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) objeto y `pMainWnd` es un puntero a la ventana se active cuando se presiona la tecla de acceso rápido, podría usar el código siguiente para asociar especificada en el control con la tecla de acceso rápido la ventana apunta `pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

Cada vez que el usuario presiona una tecla de acceso rápido global, la ventana especificada recibe un [WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand) mensaje que especifica **SC_HOTKEY** como el tipo del comando. Este mensaje también activa la ventana que lo recibe. Dado que este mensaje no incluye ninguna información en la clave exacta que se presionó, con este método no permite distinguir entre diferentes teclas de acceso directo que se pueden conectar a la misma ventana. La tecla de acceso rápido sigue siendo válida hasta que la aplicación que envió **mensaje WM_SETHOTKEY** se cierra.

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)


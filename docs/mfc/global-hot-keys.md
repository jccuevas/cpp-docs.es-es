---
title: Teclas de acceso rápido globales | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2ef1e2135ebd780938fb0ed194a93058fd010f6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209159"
---
# <a name="global-hot-keys"></a>Teclas de acceso directo globales
Tecla de acceso rápido global está asociada con una ventana no secundaria específica. Permite al usuario activar la ventana desde cualquier parte del sistema. Una aplicación establece una tecla de acceso rápido global para una ventana concreta mediante el envío de la [mensaje WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) mensaje a esa ventana. Por ejemplo, si `m_HotKeyCtrl` es el [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) objeto y `pMainWnd` es un puntero a la ventana se active cuando se presiona la tecla de acceso rápido, podría usar el código siguiente para asociar especificada en el control con la tecla de acceso rápido la ventana apunta `pMainWnd`.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 Cada vez que el usuario presiona una tecla de acceso rápido global, la ventana especificada recibe un [WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand) mensaje que especifica **SC_HOTKEY** como el tipo del comando. Este mensaje también activa la ventana que lo recibe. Dado que este mensaje no incluye ninguna información en la clave exacta que se presionó, con este método no permite distinguir entre diferentes teclas de acceso directo que se pueden conectar a la misma ventana. La tecla de acceso rápido sigue siendo válida hasta que la aplicación que envió **mensaje WM_SETHOTKEY** se cierra.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)


---
title: "Teclas de acceso rápido globales | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82297507d8725e6292def759272f48d0d63e84b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="global-hot-keys"></a>Teclas de acceso directo globales
Una tecla de acceso rápido global está asociada a una ventana no secundaria específica. Permite al usuario activar la ventana de cualquier parte del sistema. Una aplicación establece una tecla de acceso rápido global para una ventana concreta mediante el envío de la [mensaje WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) mensaje a esa ventana. Por ejemplo, si `m_HotKeyCtrl` es el [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) objeto y `pMainWnd` es un puntero a la ventana que se activa cuando se presiona la tecla de acceso rápido, podría utilizar el siguiente código para asociar especificada en el control con la tecla de acceso rápido la ventana señalada por `pMainWnd`.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 Cada vez que el usuario presiona una tecla de acceso rápido global, la ventana especificada recibe un [WM_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360) mensaje que especifica **SC_HOTKEY** como el tipo del comando. Este mensaje también activa la ventana que lo recibe. Dado que este mensaje no incluye ninguna información sobre la clave exacta que se presionó, con este método no permite distinguir entre las teclas de acceso rápido diferentes que pueden asociarse a la misma ventana. La tecla de acceso rápido sigue siendo válida hasta que la aplicación que envió **mensaje WM_SETHOTKEY** se cierra.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)


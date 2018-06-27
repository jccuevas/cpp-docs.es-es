---
title: Teclas de acceso rápido específicas del subproceso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14da7f0e5b0adbe72b6705700c1e9298751bc345
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953614"
---
# <a name="thread-specific-hot-keys"></a>Teclas de acceso rápido específicas del subproceso
Una aplicación establece una tecla de acceso rápido específicas del subproceso ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) mediante el uso de las ventanas `RegisterHotKey` función. Cuando el usuario presiona una tecla de acceso rápido específicas del subproceso, Windows envía una [WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) mensaje al principio de la cola de mensajes de un subproceso determinado. El mensaje WM_HOTKEY contiene el código de tecla virtual, el estado de desplazamiento y el identificador definido por el usuario de la tecla de acceso rápido específica que se presionó. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h. Para obtener más información sobre este método, consulte [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
 Tenga en cuenta que el estado de desplazamiento marcas utilizado en la llamada a `RegisterHotKey` no son los mismos que los devueltos por la [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) función miembro; deberá volver a traducir estos indicadores antes de llamar a `RegisterHotKey`.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)


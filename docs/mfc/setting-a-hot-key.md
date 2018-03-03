---
title: "Establecer una tecla de acceso rápido | Documentos de Microsoft"
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
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9cd52fca8415196fc1393cc49fe7830f6ca2cfd1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="setting-a-hot-key"></a>Establecer una tecla de acceso rápido
La aplicación puede usar la información proporcionada por una tecla de acceso rápido ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) control de una de dos maneras:  
  
-   Configurar una tecla de acceso rápido global para activar una ventana no secundaria enviando un [mensaje WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) mensaje en la ventana que se debe activar.  
  
-   Configurar una tecla de acceso rápido específicas del subproceso mediante una llamada a la función de Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## <a name="see-also"></a>Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)


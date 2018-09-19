---
title: Establecer una tecla de acceso rápido | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 254d7532b83a4f30c0029b2488bb0b2111cce31d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219402"
---
# <a name="setting-a-hot-key"></a>Establecer una tecla de acceso rápido
La aplicación puede usar la información proporcionada por una tecla de acceso rápido ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) control de dos maneras:  
  
-   Configurar una tecla de acceso rápido global para activar una ventana no secundaria mediante el envío de un [mensaje WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) mensaje en la ventana para activarse.  
  
-   Configurar una tecla de acceso rápido específicas del subproceso mediante una llamada a la función Windows [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## <a name="see-also"></a>Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)


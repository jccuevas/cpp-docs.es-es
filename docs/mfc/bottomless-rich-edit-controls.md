---
title: Controles Rich Edit | Documentos de Microsoft
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
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8a92b180ed44937c29cd880dea7439e0cfe20b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bottomless-rich-edit-controls"></a>Controles Rich Edit sin límite
La aplicación puede cambiar el tamaño de un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) según sea necesario para que siempre sea el mismo tamaño que su contenido. Un control rich edit admite esta funcionalidad como los denominados "sin límite" mediante el envío de su ventana primaria un [EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) recibe un mensaje de notificación cada vez que cambia el tamaño de su contenido.  
  
 Cuando se procesa la **EN_REQUESTRESIZE** mensaje de notificación, una aplicación debe cambiar el tamaño del control a las dimensiones de la manera especificada [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) estructura. Una aplicación también podría mover cualquier información cerca del control para dar cabida a cambio del control en el alto. Para cambiar el tamaño del control, puede usar el `CWnd` función [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Se puede forzar que un control rich Edit. sin límite para enviar una **EN_REQUESTRESIZE** mensaje de notificación mediante el uso de la [función miembro RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) función miembro. Este mensaje puede ser útil en el [OnSize](../mfc/reference/cwnd-class.md#onsize) controlador.  
  
 Para recibir **EN_REQUESTRESIZE** mensajes de notificación, debe habilitar la notificación mediante el `SetEventMask` función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)


---
title: Controles Rich Edit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2b08f6c04d345b4ae3ab32c6d0f17a1d8a4647
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343316"
---
# <a name="bottomless-rich-edit-controls"></a>Controles Rich Edit sin límite
La aplicación puede cambiar el tamaño de un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) según sea necesario para que siempre sea el mismo tamaño que su contenido. Un control rich edit admite esta funcionalidad como los denominados "sin límite" mediante el envío de su ventana primaria un [EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) recibe un mensaje de notificación cada vez que cambia el tamaño de su contenido.  
  
 Cuando se procesa la **EN_REQUESTRESIZE** mensaje de notificación, una aplicación debe cambiar el tamaño del control a las dimensiones de la manera especificada [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) estructura. Una aplicación también podría mover cualquier información cerca del control para dar cabida a cambio del control en el alto. Para cambiar el tamaño del control, puede usar el `CWnd` función [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Se puede forzar que un control rich Edit. sin límite para enviar una **EN_REQUESTRESIZE** mensaje de notificación mediante el uso de la [función miembro RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) función miembro. Este mensaje puede ser útil en el [OnSize](../mfc/reference/cwnd-class.md#onsize) controlador.  
  
 Para recibir **EN_REQUESTRESIZE** mensajes de notificación, debe habilitar la notificación mediante el `SetEventMask` función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)


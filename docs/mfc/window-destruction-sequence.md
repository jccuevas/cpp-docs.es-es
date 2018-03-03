---
title: "Secuencia de destrucción de ventanas | Documentos de Microsoft"
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
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b873d51f585336425537756064582eb709988f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="window-destruction-sequence"></a>Secuencia de destrucción de ventanas
En el marco de trabajo MFC, cuando el usuario cierra la ventana de marco, el valor predeterminado de la ventana [OnClose](../mfc/reference/cwnd-class.md#onclose) las llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La última función miembro se llama cuando se destruye la ventana de Windows es [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la [predeterminado](../mfc/reference/cwnd-class.md#default) miembro de la función para realizar una limpieza de Windows y por último, llama el función miembro virtual [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). El [CFrameWnd](../mfc/reference/cframewnd-class.md) implementación de `PostNcDestroy` elimina el objeto de ventana de C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Asignar y desasignar memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Vea también  
 [Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)


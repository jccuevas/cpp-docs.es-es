---
title: Secuencia de destrucción de ventanas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1c67d5a6391bbfc91bbce0d06a6bb58350e9a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="window-destruction-sequence"></a>Secuencia de destrucción de ventanas
En el marco de trabajo MFC, cuando el usuario cierra la ventana de marco, el valor predeterminado de la ventana [OnClose](../mfc/reference/cwnd-class.md#onclose) las llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La última función miembro se llama cuando se destruye la ventana de Windows es [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la [predeterminado](../mfc/reference/cwnd-class.md#default) miembro de la función para realizar una limpieza de Windows y por último, llama el función miembro virtual [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). El [CFrameWnd](../mfc/reference/cframewnd-class.md) implementación de `PostNcDestroy` elimina el objeto de ventana de C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Asignar y desasignar memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Vea también  
 [Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)


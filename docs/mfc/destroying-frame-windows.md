---
title: Destruir ventanas de marco | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1cbd96f5044626c7c3c07e8fca115c2b1dca8cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-frame-windows"></a>Destruir ventanas de marco
El marco de trabajo MFC administra la destrucción de ventanas, así como la creación de las ventanas asociadas con framework documentos y vistas. Si crea ventanas adicionales, es responsable de destruirlas.  
  
 En el marco de trabajo, cuando el usuario cierra la ventana de marco, el valor predeterminado de la ventana [OnClose](../mfc/reference/cwnd-class.md#onclose) las llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La última función miembro se llama cuando se destruye la ventana de Windows es [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la [predeterminado](../mfc/reference/cwnd-class.md#default) miembro de la función para realizar una limpieza de Windows y por último, llama el función miembro virtual [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). El [CFrameWnd](../mfc/reference/cframewnd-class.md) implementación de `PostNcDestroy` elimina el objeto de ventana de C++. Nunca debería utilizar C++ **eliminar** operador en una ventana de marco. Utilice `DestroyWindow` en su lugar.  
  
 Cuando se cierra la ventana principal, se cierra la aplicación. Si no existe se modifican los documentos que no haya guardado, el marco de trabajo muestra un cuadro de mensaje para preguntar si se deben guardar los documentos y se asegura de que se guardan los documentos adecuados si es necesario.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)


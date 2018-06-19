---
title: Destruir ventanas de marco | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81182c0e5633e19126d3036b5793de7658ad3d2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343481"
---
# <a name="destroying-frame-windows"></a>Destruir ventanas de marco
El marco de trabajo MFC administra la destrucción de ventanas, así como la creación de las ventanas asociadas con framework documentos y vistas. Si crea ventanas adicionales, es responsable de destruirlas.  
  
 En el marco de trabajo, cuando el usuario cierra la ventana de marco, el valor predeterminado de la ventana [OnClose](../mfc/reference/cwnd-class.md#onclose) las llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La última función miembro se llama cuando se destruye la ventana de Windows es [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la [predeterminado](../mfc/reference/cwnd-class.md#default) miembro de la función para realizar una limpieza de Windows y por último, llama el función miembro virtual [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). El [CFrameWnd](../mfc/reference/cframewnd-class.md) implementación de `PostNcDestroy` elimina el objeto de ventana de C++. Nunca debería utilizar C++ **eliminar** operador en una ventana de marco. Utilice `DestroyWindow` en su lugar.  
  
 Cuando se cierra la ventana principal, se cierra la aplicación. Si no existe se modifican los documentos que no haya guardado, el marco de trabajo muestra un cuadro de mensaje para preguntar si se deben guardar los documentos y se asegura de que se guardan los documentos adecuados si es necesario.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)


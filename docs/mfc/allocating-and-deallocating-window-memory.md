---
title: Asignar y desasignar memoria de ventana | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 294de3c4d4ecdfcb31f6e8c227bd8a3c6764268d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-and-deallocating-window-memory"></a>Asignar y desasignar memoria de ventana
No use C++ **eliminar** operador para destruir una ventana de marco o vista. En su lugar, llame a la `CWnd` función miembro `DestroyWindow`. Ventanas de marco, por lo tanto, se deben asignar en el montón con el operador **nueva**. Tenga cuidado al asignar ventanas de marco en el marco de pila o globalmente. Otras ventanas se deben asignar en el marco de pila siempre que sea posible.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas](../mfc/creating-windows.md)  
  
-   [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)  
  
-   [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Vea también  
 [Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)


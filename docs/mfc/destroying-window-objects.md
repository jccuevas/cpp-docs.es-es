---
title: Destruir objetos Window | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e7b8b2cf605e0f53418755b65151fd9eb2cff5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-window-objects"></a>Destruir objetos Window
Se debe tener cuidado con las ventanas secundarias propias para destruir el objeto de ventana de C++ cuando el usuario ha terminado con la ventana. Si no se destruyen estos objetos, la aplicación no recuperará su memoria. Afortunadamente, el marco de trabajo administra la destrucción de ventanas, así como la creación de ventanas de marco, vistas y cuadros de diálogo. Si crea ventanas adicionales, es responsable de destruirlas.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)  
  
-   [Asignar y desasignar memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Secuencia de creación de ventanas general](../mfc/general-window-creation-sequence.md)  
  
-   [Destruir ventanas de marco](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Vea también  
 [Objetos de ventana](../mfc/window-objects.md)


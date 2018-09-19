---
title: Destruir objetos Window | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3aacb01d945429bc36543f78e3635c39ef58223d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343381"
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


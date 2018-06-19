---
title: Desasociar CWnd de su HWND | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a776b4ff4799750c89a322379a063030db748eec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342685"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Desasociar CWnd de su HWND
Si es necesario pasar el objeto, por`HWND` relación, MFC proporciona otra `CWnd` función miembro, [separar](../mfc/reference/cwnd-class.md#detach), que desconecta el objeto de ventana de C++ de la ventana de Windows. Esto impide que el destructor destruir la ventana de Windows cuando se destruye el objeto.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas](../mfc/creating-windows.md)  
  
-   [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)  
  
-   [Asignar y desasignar memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>Vea también  
 [Objetos de ventana](../mfc/window-objects.md)


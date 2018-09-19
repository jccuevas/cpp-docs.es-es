---
title: Cuándo inicializar objetos CWnd | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee10a4632809a224028bfa482f80ed9e8a9334a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382878"
---
# <a name="when-to-initialize-cwnd-objects"></a>Cuándo inicializar los objetos CWnd
No se puede crear sus propios secundarios ventanas o llamar a las funciones de API de Windows en el constructor de un `CWnd`-objeto derivado. Esto es porque el `HWND` para el `CWnd` objeto aún no se ha creado. Inicialización de más específico de Windows, como agregar ventanas secundarias, debe realizarse dentro de un [OnCreate](../mfc/reference/cwnd-class.md#oncreate) el controlador de mensajes.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Creación de documento/vista](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)


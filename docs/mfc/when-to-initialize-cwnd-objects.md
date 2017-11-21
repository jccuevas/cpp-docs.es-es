---
title: "Cuándo inicializar objetos CWnd | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2e9d99fe2f01111308a9a7a002aeefbf472a0b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="when-to-initialize-cwnd-objects"></a>Cuándo inicializar los objetos CWnd
No se puede crear sus propios secundarios ventanas o llamar a las funciones de API de Windows en el constructor de un `CWnd`-objeto derivado. Esto es porque el `HWND` para el `CWnd` objeto aún no se ha creado. Inicialización de más específico de Windows, como agregar ventanas secundarias, debe realizarse dentro de un [OnCreate](../mfc/reference/cwnd-class.md#oncreate) el controlador de mensajes.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Creación de documento/vista](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)


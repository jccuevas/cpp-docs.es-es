---
title: Contextos de dispositivo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26d4a0e32a8b24a72447cf4227be128659316c0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="device-contexts"></a>Contextos de dispositivo
Un contexto de dispositivo es una estructura de datos de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujo se realizan a través de un objeto de contexto de dispositivo, que encapsula las API de Windows para dibujar líneas, formas y texto. Contextos de dispositivo permiten dibujar independientes del dispositivo en Windows. Contextos de dispositivo se pueden utilizar para dibujar en la pantalla, a la impresora o en un metarchivo.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md) objetos encapsulan el lenguaje común de Windows, una llamada a la `BeginPaint` función, dibujar en el contexto de dispositivo y, luego, llamar a la `EndPaint` (función). El `CPaintDC` llamadas de constructor `BeginPaint` a usted y el destructor llama `EndPaint`. El proceso simplificado es crear el [CDC](../mfc/reference/cdc-class.md) objeto dibujar y, a continuación, destruiría la `CDC` objeto. En el marco de trabajo, gran parte de este proceso se automatiza. En concreto, su `OnDraw` función se le pasa un `CPaintDC` ya preparada (a través de `OnPrepareDC`), y limita a dibujar dentro. Ser destruido por el marco de trabajo y el contexto de dispositivo subyacente queda libre para Windows tras la devolución de la llamada a su `OnDraw` función.  
  
 [CClientDC](../mfc/reference/cclientdc-class.md) objetos encapsulan trabajando con un contexto de dispositivo que representa el área de cliente de una ventana. El `CClientDC` llamadas al constructor el `GetDC` función y el destructor llama la `ReleaseDC` función. [Los objetos CWindowDC](../mfc/reference/cwindowdc-class.md) objetos encapsulan un contexto de dispositivo que representa toda la ventana, incluido su marco.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md) objetos encapsulan el dibujo en un metarchivo de Windows. Contrasta con la `CPaintDC` pasado a `OnDraw`, en este caso debe llamar a [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) usted mismo.  
  
## <a name="mouse-drawing"></a>Dibujar con el mouse  
 Mayor parte del dibujo en un programa marco y, por tanto, la mayoría del trabajo contexto de dispositivo, se realiza en la vista `OnDraw` función miembro. Sin embargo, todavía puede usar objetos en el contexto de dispositivo para otros fines. Por ejemplo, para proporcionar comentarios de seguimiento de movimiento del mouse en una vista, debe dibujar directamente en la vista sin tener que esperar `OnDraw` para llamarlo.  
  
 En tal caso, puede usar un [CClientDC](../mfc/reference/cclientdc-class.md) objeto de contexto de dispositivo para dibujar directamente en la vista.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Contextos de dispositivo (definición)](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [Dibujo en una vista](../mfc/drawing-in-a-view.md)  
  
-   [Interpretación de la entrada del usuario a través de una vista](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [Líneas y curvas](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [Formas rellenas](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [Fuentes y texto](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [Colores](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [Espacios de coordenadas y transformaciones](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>Vea también  
 [Objetos de ventana](../mfc/window-objects.md)


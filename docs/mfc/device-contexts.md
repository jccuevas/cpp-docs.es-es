---
title: Contextos de dispositivo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efda2666a1d7cf47a485a9e1ceb53c09f4966989
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203837"
---
# <a name="device-contexts"></a>Contextos de dispositivo
Un contexto de dispositivo es una estructura de datos de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujos se realizan a través de un objeto de contexto de dispositivo, que encapsula las API de Windows para dibujar líneas, formas y texto. Contextos de dispositivo permiten dibujos independientes de dispositivo en Windows. Contextos de dispositivo pueden utilizarse para dibujar en la pantalla, a la impresora o en un metarchivo.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md) objetos encapsulan la expresión común de Windows, una llamada a la `BeginPaint` función, dibujar en el contexto de dispositivo y, luego, llamar a la `EndPaint` función. El `CPaintDC` llamadas de constructor `BeginPaint` para usted y el destructor llama a `EndPaint`. Es el proceso simplificado crear el [CDC](../mfc/reference/cdc-class.md) objeto, dibujar y, a continuación, destruya el `CDC` objeto. En el marco de trabajo, se automatiza gran parte de este proceso. En concreto, su `OnDraw` función se pasa un `CPaintDC` ya preparado (a través de `OnPrepareDC`), y simplemente dibuje en él. Se destruye el marco de trabajo y se libera el contexto de dispositivo subyacente para Windows tras la devolución de la llamada a su `OnDraw` función.  
  
 [CClientDC](../mfc/reference/cclientdc-class.md) objetos encapsulan trabajando con un contexto de dispositivo que representa el área de cliente de una ventana. El `CClientDC` constructor llama a la `GetDC` función y el destructor llama a la `ReleaseDC` función. [CWindowDC](../mfc/reference/cwindowdc-class.md) objetos encapsulan un contexto de dispositivo que representa la ventana completa, incluido su marco.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md) objetos encapsulan el dibujo en un metarchivo de Windows. Por el contrario el `CPaintDC` pasado a `OnDraw`, en este caso debe llamar a [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) usted mismo.  
  
## <a name="mouse-drawing"></a>Dibujar con el mouse  
 La mayoría de dibujo en un programa de framework y, por tanto, la mayoría del trabajo contexto de dispositivo, se realiza en la vista `OnDraw` función miembro. Sin embargo, todavía puede usar los objetos de contexto de dispositivo para otros fines. Por ejemplo, para proporcionar comentarios de seguimiento para el movimiento del mouse en una vista, necesita dibujar directamente en la vista sin esperar `OnDraw` llamarse.  
  
 En tal caso, puede usar un [CClientDC](../mfc/reference/cclientdc-class.md) objeto de contexto de dispositivo para dibujar directamente en la vista.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre  
  
-   [Contextos de dispositivo (definición)](https://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [Dibujo en una vista](../mfc/drawing-in-a-view.md)  
  
-   [Interpretación de la entrada del usuario a través de una vista](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [Líneas y curvas](https://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [Formas rellenas](https://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [Fuentes y texto](/windows/desktop/gdi/fonts-and-text)  
  
-   [Colores](https://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [Espacios de coordenadas y transformaciones](https://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>Vea también  
 [Objetos de ventana](../mfc/window-objects.md)


---
title: Contextos de dispositivo
ms.date: 11/04/2016
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
ms.openlocfilehash: d5337e8d8b83a641458a15612803feeec3b6361c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508657"
---
# <a name="device-contexts"></a>Contextos de dispositivo

Un contexto de dispositivo es una estructura de datos de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujo se realizan a través de un objeto de contexto de dispositivo, que encapsula las API de Windows para dibujar líneas, formas y texto. Los contextos de dispositivo permiten dibujar en Windows de manera independiente del dispositivo. Los contextos de dispositivo se pueden usar para dibujar en la pantalla, en la impresora o en un metarchivo.

Los objetos [CPaintDC](../mfc/reference/cpaintdc-class.md) encapsulan la expresión común de Windows, llama `BeginPaint` a la función, dibujan en el contexto del dispositivo y `EndPaint` , a continuación, llaman a la función. El `CPaintDC` constructor llama `BeginPaint` a para usted y el destructor llama `EndPaint`a. El proceso simplificado es crear el objeto [CDC](../mfc/reference/cdc-class.md) , dibujar y, a continuación, `CDC` destruir el objeto. En el marco de trabajo, gran parte de este proceso es automático. En concreto, se `OnDraw` pasa a la función `CPaintDC` una ya preparada ( `OnPrepareDC`a través de) y simplemente se dibuja en ella. El marco de trabajo lo destruye y el contexto del dispositivo subyacente se libera a Windows al volver de la llamada a `OnDraw` la función.

Los objetos [CClientDC (](../mfc/reference/cclientdc-class.md) encapsulan el trabajo con un contexto de dispositivo que solo representa el área de cliente de una ventana. El `CClientDC` constructor llama a `GetDC` la función y el destructor llama a `ReleaseDC` la función. Los objetos [CWindowDC](../mfc/reference/cwindowdc-class.md) encapsulan un contexto de dispositivo que representa toda la ventana, incluido su marco.

Los objetos [cmetafiledc (](../mfc/reference/cmetafiledc-class.md) encapsulan el dibujo en un metarchivo de Windows. A diferencia de lo `CPaintDC` que se `OnDraw`pasa a, en este caso se debe llamar a [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) personalmente.

## <a name="mouse-drawing"></a>Dibujo del mouse

La mayoría del dibujo en un programa de Framework (y, por tanto, la mayor parte del trabajo de `OnDraw` contexto del dispositivo) se realiza en la función miembro de la vista. Sin embargo, todavía puede usar objetos de contexto de dispositivo para otros propósitos. Por ejemplo, para proporcionar comentarios de seguimiento para el movimiento del mouse en una vista, debe dibujar directamente en la vista sin esperar `OnDraw` a que se llame a.

En tal caso, puede usar un objeto de contexto de dispositivo [CClientDC (](../mfc/reference/cclientdc-class.md) para dibujar directamente en la vista.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Contextos de dispositivo (definición)](/windows/win32/gdi/device-contexts)

- [Dibujo en una vista](../mfc/drawing-in-a-view.md)

- [Interpretación de la entrada del usuario a través de una vista](../mfc/interpreting-user-input-through-a-view.md)

- [Líneas y curvas](/windows/win32/gdi/lines-and-curves)

- [Formas rellenas](/windows/win32/gdi/filled-shapes)

- [Fuentes y texto](/windows/win32/gdi/fonts-and-text)

- [Colores](/windows/win32/gdi/colors)

- [Espacios de coordenadas y transformaciones](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)

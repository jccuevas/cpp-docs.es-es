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
ms.openlocfilehash: a5be2e57302e597e9c65b7bc966a5ff0ecaf855a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620363"
---
# <a name="device-contexts"></a>Contextos de dispositivo

Un contexto de dispositivo es una estructura de datos de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujo se realizan a través de un objeto de contexto de dispositivo, que encapsula las API de Windows para dibujar líneas, formas y texto. Los contextos de dispositivo permiten dibujar en Windows de manera independiente del dispositivo. Los contextos de dispositivo se pueden usar para dibujar en la pantalla, en la impresora o en un metarchivo.

Los objetos [CPaintDC](reference/cpaintdc-class.md) encapsulan la expresión común de Windows, llama a la `BeginPaint` función, dibujan en el contexto del dispositivo y, a continuación, llaman a la `EndPaint` función. El `CPaintDC` constructor llama a `BeginPaint` para usted y el destructor llama a `EndPaint` . El proceso simplificado es crear el objeto [CDC](reference/cdc-class.md) , dibujar y, a continuación, destruir el `CDC` objeto. En el marco de trabajo, gran parte de este proceso es automático. En concreto, `OnDraw` se pasa a la función una `CPaintDC` ya preparada (a través de `OnPrepareDC` ) y simplemente se dibuja en ella. El marco de trabajo lo destruye y el contexto del dispositivo subyacente se libera a Windows al volver de la llamada a la `OnDraw` función.

Los objetos [CClientDC (](reference/cclientdc-class.md) encapsulan el trabajo con un contexto de dispositivo que solo representa el área de cliente de una ventana. El `CClientDC` constructor llama a la `GetDC` función y el destructor llama a la `ReleaseDC` función. Los objetos [CWindowDC](reference/cwindowdc-class.md) encapsulan un contexto de dispositivo que representa toda la ventana, incluido su marco.

Los objetos [cmetafiledc (](reference/cmetafiledc-class.md) encapsulan el dibujo en un metarchivo de Windows. A diferencia de lo que `CPaintDC` se pasa a `OnDraw` , en este caso se debe llamar a [OnPrepareDC](reference/cview-class.md#onpreparedc) personalmente.

## <a name="mouse-drawing"></a>Dibujo del mouse

La mayoría del dibujo en un programa de Framework (y, por tanto, la mayor parte del trabajo de contexto del dispositivo) se realiza en la función miembro de la vista `OnDraw` . Sin embargo, todavía puede usar objetos de contexto de dispositivo para otros propósitos. Por ejemplo, para proporcionar comentarios de seguimiento para el movimiento del mouse en una vista, debe dibujar directamente en la vista sin esperar `OnDraw` a que se llame a.

En tal caso, puede usar un objeto de contexto de dispositivo [CClientDC (](reference/cclientdc-class.md) para dibujar directamente en la vista.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Contextos de dispositivo (definición)](/windows/win32/gdi/device-contexts)

- [Dibujo en una vista](drawing-in-a-view.md)

- [Interpretación de la entrada del usuario a través de una vista](interpreting-user-input-through-a-view.md)

- [Líneas y curvas](/windows/win32/gdi/lines-and-curves)

- [Formas rellenas](/windows/win32/gdi/filled-shapes)

- [Fuentes y texto](/windows/win32/gdi/fonts-and-text)

- [Colores](/windows/win32/gdi/colors)

- [Espacios de coordenadas y transformaciones](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Consulte también

[Window (Objetos)](window-objects.md)

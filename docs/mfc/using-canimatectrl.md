---
title: Usar CAnimateCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 79c1a0111317514ef6fd68acd0c6a2ebdccc3ba4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447105"
---
# <a name="using-canimatectrl"></a>Usar CAnimateCtrl

Un control de animación, representado por la clase [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), es una ventana que muestra un clip en formato de audio de vídeo intercalado (AVI), el formato de vídeo/audio estándar de Windows. Un clip AVI es una serie de fotogramas de mapa de bits, como una película.

Dado que el subproceso continúa ejecutándose mientras se muestra el clip AVI, un uso común de un control de animación es indicar la actividad del sistema durante una operación larga. Por ejemplo, el cuadro de diálogo Buscar de Windows muestra una lupa en movimiento mientras el sistema busca un archivo.

Los controles de animación solo pueden reproducir clips AVI sencillos y no admiten sonido. (Para obtener una lista completa de las limitaciones, vea [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)). Dado que las capacidades de un control de animación están muy limitadas y están sujetas a cambios, debe usar una alternativa como el control MCIWnd si necesita un control para proporcionar capacidades de reproducción o grabación multimedia. Para obtener más información sobre el control MCIWnd, consulte la documentación multimedia.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Uso de un control de animación](../mfc/using-an-animation-control.md)

- [Notificaciones enviadas por los controles de animación](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Consulte también

[Controles](../mfc/controls-mfc.md)

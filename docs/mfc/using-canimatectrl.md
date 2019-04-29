---
title: Usar CAnimateCtrl
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: b967cc6dde6b4f639ef081b3821f6a7e5a2fe295
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351646"
---
# <a name="using-canimatectrl"></a>Usar CAnimateCtrl

Un control de animación, representado por la clase [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), es una ventana que muestra un clip en formato de Audio Video Interleaved (AVI), el formato de audio y vídeo de Windows estándar. Un clip AVI es una serie de marcos de mapa de bits, como una película.

Puesto que el subproceso continúa ejecutándose mientras se muestra el clip AVI, un uso común de un control de animación es indicar la actividad del sistema durante una operación larga. Por ejemplo, el cuadro de diálogo Buscar de Windows muestra una lupa móvil como el sistema busca un archivo.

Los controles de animación sólo pueden reproducir clips AVI sencillos y no admiten sonido. (Para obtener una lista completa de limitaciones, consulte [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Dado que las capacidades de un control de animación se ve limitadas y está sujeta a cambios, debe usar una alternativa como el control MCIWnd si necesita un control para proporcionar la reproducción multimedia y capacidad de grabación. Para obtener más información sobre el control MCIWnd, consulte la documentación multimedia.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Uso de un control de animación](../mfc/using-an-animation-control.md)

- [Notificaciones enviadas por los controles de animación](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)

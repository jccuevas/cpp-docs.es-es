---
title: Usar CAnimateCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f27fd24c3c4334476c78ba0b59c90cbbb0d51f5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-canimatectrl"></a>Usar CAnimateCtrl
Un control de animación, representado por la clase [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), es una ventana que muestra un clip en formato de Audio Video Interleaved (AVI): el formato de audio/vídeo de Windows estándar. Un clip AVI es una serie de marcos de mapa de bits, como una película.  
  
 Puesto que el subproceso continúa ejecutándose mientras se muestra el clip AVI, un uso común de un control de animación es indicar la actividad del sistema durante una operación larga. Por ejemplo, el cuadro de diálogo Buscar de Windows muestra una lupa móvil como el sistema busca un archivo.  
  
 Controles de animación sólo pueden reproducir clips AVI sencillos y no admiten sonido. (Para obtener una lista completa de limitaciones, vea [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Puesto que las capacidades de un control de animación están bastante limitadas y sujeta a cambios, debe usar una alternativa como el control MCIWnd si necesita un control para proporcionar capacidades de grabación o de reproducción multimedia. Para obtener más información sobre el control MCIWnd, vea la documentación multimedia.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Uso de un control de animación](../mfc/using-an-animation-control.md)  
  
-   [Notificaciones enviadas por los controles de animación](../mfc/notifications-sent-by-animation-controls.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles](../mfc/controls-mfc.md)


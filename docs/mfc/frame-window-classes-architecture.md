---
title: Clases de ventana de marco (Arquitectura)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: e3ae432c1adc881a5c67d6a6c292dc1f6a583ab3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441254"
---
# <a name="frame-window-classes-architecture"></a>Clases de ventana de marco (Arquitectura)

En la arquitectura de documento/vista, las ventanas de marco son ventanas que contienen una ventana de vista. También admiten tener barras de control asociadas.

En las aplicaciones de interfaz de múltiples documentos (MDI), la ventana principal se deriva de `CMDIFrameWnd`. Contiene indirectamente los marcos de los documentos, que son `CMDIChildWnd` objetos. Los objetos `CMDIChildWnd`, a su vez, contienen las vistas de los documentos.

En las aplicaciones de interfaz de un único documento (SDI), la ventana principal, derivada de `CFrameWnd`, contiene la vista del documento actual.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
La clase base para la ventana de marco principal de la aplicación SDI. También es la clase base para todas las demás clases de ventana de marco.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
La clase base para la ventana de marco principal de una aplicación MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
La clase base para las ventanas de marco de documento de una aplicación MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Proporciona la ventana de marco para una vista cuando se está editando un documento de servidor en su lugar.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)

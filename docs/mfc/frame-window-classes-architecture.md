---
title: Clases de ventana de marco (Arquitectura)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: d1022d9a49e12585a6588e7b3202155f533e4706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431712"
---
# <a name="frame-window-classes-architecture"></a>Clases de ventana de marco (Arquitectura)

En la arquitectura documento/vista, ventanas de marco son ventanas que contienen una ventana de vista. También admiten la necesidad de controlar barras asociadas a ellos.

En aplicaciones de múltiples documentos (MDI) de la interfaz, se deriva de la ventana principal `CMDIFrameWnd`. Indirectamente contiene marcos de los documentos, que son `CMDIChildWnd` objetos. El `CMDIChildWnd` objetos, a su vez, contienen vistas de los documentos.

En las aplicaciones de único documento (SDI) de la interfaz, la ventana principal, derivado de `CFrameWnd`, contiene la vista del documento actual.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
La clase base para la ventana de marco principal de una aplicación SDI. También es la clase base para todas las demás clases de ventana de marco.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
La clase base para la ventana de marco principal de una aplicación MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
La clase base para las ventanas de marco de documento de una aplicación MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Proporciona la ventana de marco para obtener una vista cuando se está editando un documento de servidor en su lugar.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)


---
title: Clases de ventana de marco (Arquitectura)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: 483112d197b7c7211989ecda8b774deb9f30d49e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624607"
---
# <a name="frame-window-classes-architecture"></a>Clases de ventana de marco (Arquitectura)

En la arquitectura de documento/vista, las ventanas de marco son ventanas que contienen una ventana de vista. También admiten tener barras de control asociadas.

En aplicaciones de interfaz de múltiples documentos (MDI), la ventana principal se deriva de `CMDIFrameWnd` . Contiene indirectamente los marcos de los documentos, que son `CMDIChildWnd` objetos. Los `CMDIChildWnd` objetos, a su vez, contienen las vistas de los documentos.

En las aplicaciones de interfaz de un único documento (SDI), la ventana principal, derivada de `CFrameWnd` , contiene la vista del documento actual.

[CFrameWnd](reference/cframewnd-class.md)<br/>
La clase base para la ventana de marco principal de la aplicación SDI. También es la clase base para todas las demás clases de ventana de marco.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
La clase base para la ventana de marco principal de una aplicación MDI.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
La clase base para las ventanas de marco de documento de una aplicación MDI.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Proporciona la ventana de marco para una vista cuando se está editando un documento de servidor en su lugar.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)

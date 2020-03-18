---
title: Clases de barra de control
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: a050c5d2f7396324c2c380a03fc28e01ab992208
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440963"
---
# <a name="control-bar-classes"></a>Clases de barra de control

Las barras de control se adjuntan a una ventana de marco. Contienen botones, paneles de estado o una plantilla de cuadro de diálogo. Las barras de control de punto flotante, también denominadas paletas de herramientas, se implementan mediante su asociación a un objeto [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) .

## <a name="framework-control-bars"></a>Barras de control de marco

Estas barras de control son una parte integral del marco de trabajo de MFC. Son más fáciles de usar y más eficaces que las barras de control de Windows, ya que se integran con el marco. La mayoría de las aplicaciones MFC usan estas barras de control en lugar de las barras de control de Windows.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
La clase base para las barras de control de MFC enumeradas en esta sección. Una barra de control es una ventana alineada en el borde de una ventana de marco. La barra de control contiene controles secundarios basados en `HWND`o controles no basados en un `HWND`, como los botones de la barra de herramientas.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Barra de control que se basa en una plantilla de cuadro de diálogo.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Admite una barra de herramientas que puede contener ventanas secundarias adicionales en forma de controles.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Ventanas de control de barra de herramientas que contienen botones de comando de mapa de bits no basados en un `HWND`. La mayoría de las aplicaciones MFC utilizan esta clase en lugar de `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
La clase base para las ventanas de control de barra de estado. La mayoría de las aplicaciones MFC utilizan esta clase en lugar de `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Barras de control de Windows

Estas barras de control son contenedores finos para los controles de Windows correspondientes. Dado que no se integran con el marco, son más difíciles de usar que las barras de control mencionadas anteriormente. La mayoría de las aplicaciones MFC usan las barras de control mencionadas anteriormente.

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implementa el control interno del objeto `CRebar`.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Una ventana horizontal, normalmente dividida en paneles, en la que una aplicación puede mostrar información de estado.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Proporciona la funcionalidad del control de barra de herramientas común de Windows.

## <a name="related-classes"></a>Clases relacionadas

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Pequeña ventana emergente que muestra una sola línea de texto que describe el propósito de una herramienta en una aplicación.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Controla el almacenamiento persistente de datos de estado de acoplamiento para las barras de control.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)

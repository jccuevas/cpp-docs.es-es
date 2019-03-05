---
title: Clases de barra de control
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: 3426d84eab888a6fe78b663945776fff2fe708dd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302252"
---
# <a name="control-bar-classes"></a>Clases de barra de control

Barras de control se adjuntan a una ventana de marco. Contienen botones, paneles de estado o una plantilla de cuadro de diálogo. Barras de controles flotantes, también denominadas las paletas de herramientas, se implementan mediante la asociación a un [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) objeto.

## <a name="framework-control-bars"></a>Barras de Control de marco de trabajo

Estas barras de control son una parte integral del marco de trabajo MFC. Son más fáciles de usar y más eficaces que las barras de control de la Windows porque se integran con el marco de trabajo. La mayoría de las aplicaciones de MFC utilizan estas barras de control, en lugar de las barras de control de Windows.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
La clase base para las barras de control MFC enumerados en esta sección. Una barra de controles es una ventana que se alinea con el borde de una ventana de marco. Contiene la barra de control `HWND`-en función de los controles secundarios o controles no basados en un `HWND`, como los botones de barra de herramientas.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Una barra de controles que se basa en una plantilla de cuadro de diálogo.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Es compatible con una barra de herramientas que puede contener ventanas secundarias adicionales en forma de controles.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Ventanas de control de barra de herramientas que contienen botones de comando de mapa de bits no según una `HWND`. La mayoría de las aplicaciones de MFC utilizan esta clase en lugar de `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
La clase base para las ventanas de control de barra de estado. La mayoría de las aplicaciones de MFC utilizan esta clase en lugar de `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Barras de Control de Windows

Estas barras de control son contenedores finos para los controles de Windows correspondientes. Puesto que no están integradas con el marco de trabajo, son más difíciles de usar que las barras de control enumeradas anteriormente. La mayoría de las aplicaciones de MFC use las barras de control enumeradas anteriormente.

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implementa el control interno de la `CRebar` objeto.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Una ventana horizontal, que normalmente se divide en paneles, en el que una aplicación puede mostrar información de estado.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Proporciona la funcionalidad del control de barra de herramientas común de Windows.

## <a name="related-classes"></a>Clases relacionadas

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Una pequeña ventana emergente que muestra una sola línea de texto que describe el propósito de una herramienta en una aplicación.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Controla el almacenamiento persistente de datos de estado de las barras de control de acoplamiento.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

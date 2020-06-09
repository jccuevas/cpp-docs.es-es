---
title: Clases de barra de control
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: f89770683edb1f4268b4f19adb74e5c08aa5f109
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620527"
---
# <a name="control-bar-classes"></a>Clases de barra de control

Las barras de control se adjuntan a una ventana de marco. Contienen botones, paneles de estado o una plantilla de cuadro de diálogo. Las barras de control de punto flotante, también denominadas paletas de herramientas, se implementan mediante su asociación a un objeto [CMiniFrameWnd](reference/cminiframewnd-class.md) .

## <a name="framework-control-bars"></a>Barras de control de marco

Estas barras de control son una parte integral del marco de trabajo de MFC. Son más fáciles de usar y más eficaces que las barras de control de Windows, ya que se integran con el marco. La mayoría de las aplicaciones MFC usan estas barras de control en lugar de las barras de control de Windows.

[CControlBar](reference/ccontrolbar-class.md)<br/>
La clase base para las barras de control de MFC enumeradas en esta sección. Una barra de control es una ventana alineada en el borde de una ventana de marco. La barra de control contiene `HWND` controles secundarios basados en o controles no basados en, como los botones de la `HWND` barra de herramientas.

[CDialogBar](reference/cdialogbar-class.md)<br/>
Barra de control que se basa en una plantilla de cuadro de diálogo.

[CReBar](reference/crebar-class.md)<br/>
Admite una barra de herramientas que puede contener ventanas secundarias adicionales en forma de controles.

[CToolBar](reference/ctoolbar-class.md)<br/>
Ventanas de control de barra de herramientas que contienen botones de comando de mapa de bits no basados en `HWND` . La mayoría de las aplicaciones MFC usan esta clase en lugar de `CToolBarCtrl` .

[CStatusBar](reference/cstatusbar-class.md)<br/>
La clase base para las ventanas de control de barra de estado. La mayoría de las aplicaciones MFC usan esta clase en lugar de `CStatusBarCtrl` .

## <a name="windows-control-bars"></a>Barras de control de Windows

Estas barras de control son contenedores finos para los controles de Windows correspondientes. Dado que no se integran con el marco, son más difíciles de usar que las barras de control mencionadas anteriormente. La mayoría de las aplicaciones MFC usan las barras de control mencionadas anteriormente.

[CRebarCtrl](reference/crebarctrl-class.md)<br/>
Implementa el control interno del `CRebar` objeto.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Una ventana horizontal, normalmente dividida en paneles, en la que una aplicación puede mostrar información de estado.

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Proporciona la funcionalidad del control de barra de herramientas común de Windows.

## <a name="related-classes"></a>Clases relacionadas

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Pequeña ventana emergente que muestra una sola línea de texto que describe el propósito de una herramienta en una aplicación.

[CDockState](reference/cdockstate-class.md)<br/>
Controla el almacenamiento persistente de datos de estado de acoplamiento para las barras de control.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)

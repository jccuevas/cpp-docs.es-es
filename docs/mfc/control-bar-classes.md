---
title: Clases de barra de control | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.control
dev_langs: C++
helpviewer_keywords: control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44fcecbf1d7ddb6c46469f25349d972c8b317809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="control-bar-classes"></a>Clases de barra de control
Barras de control están conectadas a una ventana de marco. Contienen botones, paneles de estado o una plantilla de cuadro de diálogo. Barras de control flotantes, también denominadas las paletas de herramientas, se implementan mediante una asociación a una [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) objeto.  
  
## <a name="framework-control-bars"></a>Barras de Control de marco de trabajo  
 Estas barras de control son una parte integral del marco de trabajo MFC. Son fáciles de usar y más eficaces que las ventanas de las barras de control porque se integran con el marco de trabajo. La mayoría de las aplicaciones de MFC utilizan estas barras de control en lugar de las barras de control de Windows.  
  
 [CControlBar](../mfc/reference/ccontrolbar-class.md)  
 La clase base para las barras de control MFC enumerados en esta sección. Una barra de controles es una ventana que se alinea con el borde de una ventana de marco. La barra de control contiene `HWND`-según los controles secundarios o controles no basados en un `HWND`, como los botones de barra de herramientas.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Una barra de controles que se basa en una plantilla de cuadro de diálogo.  
  
 [CReBar](../mfc/reference/crebar-class.md)  
 Es compatible con una barra de herramientas que puede contener ventanas secundarias adicionales en forma de controles.  
  
 [CToolBar](../mfc/reference/ctoolbar-class.md)  
 Ventanas de control de barra de herramientas que contienen botones de comando de mapa de bits no se basa en un `HWND`. La mayoría de las aplicaciones de MFC utilizan esta clase en lugar de `CToolBarCtrl`.  
  
 [CStatusBar](../mfc/reference/cstatusbar-class.md)  
 La clase base para ventanas de control de barra de estado. La mayoría de las aplicaciones de MFC utilizan esta clase en lugar de `CStatusBarCtrl`.  
  
## <a name="windows-control-bars"></a>Barras de Control de Windows  
 Estas barras de control son contenedores finos para los controles de Windows correspondientes. Dado que no se integran con el marco de trabajo, son más difíciles de usar que los de las barras de control enumeradas anteriormente. La mayoría de las aplicaciones de MFC utilizan las barras de control enumeradas anteriormente.  
  
 [CRebarCtrl](../mfc/reference/crebarctrl-class.md)  
 Implementa el control interno de la `CRebar` objeto.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Ventana horizontal, que normalmente se divide en paneles, en el que una aplicación puede mostrar información de estado.  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Proporciona la funcionalidad del control de barra de herramientas común de Windows.  
  
## <a name="related-classes"></a>Clases relacionadas  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Una pequeña ventana emergente que muestra una sola línea de texto que describe el propósito de una herramienta de una aplicación.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Controla el almacenamiento persistente de datos de estado para las barras de control de acoplamiento.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)


---
title: "Clases de barra de control | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "barras de control, clases"
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de barra de control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las barras de control se asocian a una ventana de marco.  Contienen botones, los paneles de estado, o una plantilla de cuadro de diálogo.  Las barras de control Libre\- flotantes, también denominadas paletas de la herramienta, se implementan adjuntandolas a un objeto de [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) .  
  
## Barras de controles del marco  
 Estas barras de control son una parte integral de MFC.  Son más fáciles de utilizar y más eficaces que las barras de control de Windows porque se integran con el marco.  La mayoría de las aplicaciones MFC utilizan estas barras de controles en lugar de las barras de controles de Windows.  
  
 [CControlBar](../mfc/reference/ccontrolbar-class.md)  
 La clase base para las barras de control MFC enumeradas en esta sección.  Una barra de controles es una ventana alineada con el borde de una ventana de marco.  Barra de control contiene `HWND`\- controles secundarios o controles basados en no basados en `HWND`, como botones de la barra de herramientas.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Una barra de control basado en una plantilla de cuadro de diálogo.  
  
 [CReBar](../mfc/reference/crebar-class.md)  
 Admite una barra de herramientas que puede contener las ventanas secundarias adicionales en forma de controles.  
  
 [CToolBar](../mfc/reference/ctoolbar-class.md)  
 Ventanas de control toolbar que contienen botones de comando bitmap no basados en `HWND`.  La mayoría de las aplicaciones MFC utilizan esta clase en lugar de `CToolBarCtrl`.  
  
 [CStatusBar](../mfc/reference/cstatusbar-class.md)  
 La clase base para las ventanas de control de la barra de estado.  La mayoría de las aplicaciones MFC utilizan esta clase en lugar de `CStatusBarCtrl`.  
  
## Barras de controles de Windows  
 Estas barras de control son contenedores finos para los controles correspondientes de Windows.  Porque no se integran con el marco, son más difíciles de utilizar que las barras de control enumeradas anteriormente.  La mayoría de las aplicaciones MFC utilizan barras de control enumeradas anteriormente.  
  
 [CRebarCtrl](../mfc/reference/crebarctrl-class.md)  
 Implementa el control interno del objeto de `CRebar` .  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Una ventana horizontal, divide normalmente en los paneles, donde una aplicación puede mostrar información de estado.  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Proporciona la funcionalidad del control de barra de herramientas común de Windows.  
  
## Clases relacionadas  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Una pequeña ventana emergente que muestra una única línea de texto que describe el propósito de una herramienta de una aplicación.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Controla el almacenamiento permanente de los datos de estado de vinculación de las barras de control.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)
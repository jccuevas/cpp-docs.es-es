---
title: "Introduction to ATL Window Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "window classes"
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Introduction to ATL Window Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las siguientes clases de ATL están diseñados para implementar y manipular las ventanas:  
  
-   [CWindow](../atl/reference/cwindow-class.md) permite asociar un identificador de ventana al objeto de `CWindow` .  Se llama a los métodos de `CWindow` para manipular la ventana.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) permite implementar una nueva ventana y mensajes de proceso con un mapa de mensajes.  Puede crear una ventana basada en una clase de Windows, crear utiliza una clase existente, o crear subclases de una ventana existente.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) permite implementar un cuadro de diálogo modal o no modal y mensajes de proceso con un mapa de mensajes.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) es una clase pregeneradas que implementa una ventana cuyo mapa de mensajes se contiene en otra clase.  Mediante `CContainedWindowT` permite centralice el procesamiento de mensajes en una clase.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) permite implementar un cuadro de diálogo \(modal o no modal\) que los controles ActiveX de hospeda.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) permite implementar un cuadro de diálogo modal con funcionalidad básica.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) permite implementar una ventana que hospeda un control ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) permite implementar una ventana que hospeda un control ActiveX con licencia.  
  
 Además de las clases de ventana específicas, ATL proporciona varias clases diseñadas para crear la implementación de un objeto en la ventana de ATL más fácil.  Son las siguientes:  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) administra la información de una nueva clase de ventana.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) y [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) proporcionan un método sencillo para normalizar los rasgos de un objeto en la ventana de ATL.  
  
## Vea también  
 [Clases de ventanas](../atl/atl-window-classes.md)
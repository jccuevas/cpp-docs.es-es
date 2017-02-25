---
title: "Administrar ventanas secundarias MDI | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MDICLIENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ventanas secundarias"
  - "ventanas secundarias, y ventana MDICLIENT"
  - "ventanas de marco [C++], ventanas secundarias MDI"
  - "MDI [C++], ventanas secundarias"
  - "MDI [C++], ventanas de marco"
  - "ventana MDICLIENT"
  - "ventanas [C++], MDI"
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Administrar ventanas secundarias MDI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las ventanas de marco principal MDI \(una por la aplicación\) contienen una ventana secundaria especial denominada la ventana de **MDICLIENT** .  La ventana de **MDICLIENT** administra el área cliente de la ventana de marco principal, y al propio tiene ventanas secundarias: las ventanas de documento, derivadas de `CMDIChildWnd`.  Dado que las ventanas de documento son ventanas propios de marco \(las ventanas MDI secundarias\), también pueden tener sus propios elementos secundarios.  En todos estos casos, la ventana primaria administrar las ventanas secundarias y transmite a algunos comandos ellas.  
  
 En una ventana de marco MDI, la ventana de marco administra la ventana de **MDICLIENT** , colocándola de nuevo junto con las barras de controles.  La ventana de **MDICLIENT** , a su vez, administra todas las ventanas secundarias de marco MDI.  La ilustración siguiente muestra la relación entre una ventana de marco MDI, su ventana de **MDICLIENT** , y las ventanas secundarias de marco de documento.  
  
 ![Ventanas secundarias en una ventana de marco MDI](../mfc/media/vc37gb1.png "vc37GB1")  
Ventanas marco de MDI y ventanas secundarias  
  
 Una ventana de marco MDI también funciona junto con la ventana secundaria actual de MDI, si la hay.  La ventana de marco MDI delega mensajes de comando al elemento secundario de MDI antes de intentar controlarlos propio.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Estilos de la Cuadro\-ventana](../mfc/frame-window-styles-cpp.md)  
  
## Vea también  
 [Usar ventanas de marco](../mfc/using-frame-windows.md)
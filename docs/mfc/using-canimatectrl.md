---
title: "Usar CAnimateCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAnimateCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles de animación [C++], CAnimateCtrl (clase)"
  - "CAnimateCtrl (clase), acerca de la clase CAnimateCtrl"
  - "controles [MFC], animación"
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Usar CAnimateCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control de animación, representado por la clase [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), es una ventana que muestra clip en formato de \(AVI\) de formato AVI — vídeo y el formato de audio estándar de Windows.  AVI recorte es ejecuciones de marcos bitmap, como una película.  
  
 Puesto que el subproceso continúa ejecutándose mientras se muestra AVI recorte, un uso común de un control de la animación es indicar la actividad del sistema durante una operación larga.  Por ejemplo, el cuadro de diálogo de búsqueda de Windows muestra una lupa móvil como las búsquedas del sistema para un archivo.  
  
 Los controles de animación pueden reproducir sólo los fragmentos simples de AVI, y no admiten el sonido. \(Para obtener una lista completa de limitaciones, vea [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).\) Las características de una animación se limitan gravemente y en cambio, debe usar una alternativa como el control de MCIWnd si necesita un control proporcionar funciones multimedia de reproducción y\/o de grabación.  Para obtener más información sobre el control de MCIWnd, vea la documentación multimedia.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Utilizar un Control de animación](../mfc/using-an-animation-control.md)  
  
-   [Notificaciones Sent por Controles de animación](../mfc/notifications-sent-by-animation-controls.md)  
  
## Vea también  
 [Controles](../mfc/controls-mfc.md)
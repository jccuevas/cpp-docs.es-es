---
title: "Implementaci&#243;n de barra de estado en MFC | Microsoft Docs"
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
  - "COldStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COldStatusBar (clase)"
  - "CStatusBar (clase), y CStatusBarCtrl (clase)"
  - "CStatusBar (clase), y barras de estado MFC"
  - "CStatusBarCtrl (clase), y CStatusBar (clase)"
  - "CStatusBarCtrl (clase), y barras de estado MFC"
  - "barras de estado, y CStatusBarCtrl (clase)"
  - "barras de estado, compatibilidad con versiones anteriores"
  - "barras de estado, implementar en MFC"
  - "barras de estado, antiguas con la clase COldStatusBar"
  - "barras de estado, implementación de Windows 95"
  - "indicadores de estado"
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementaci&#243;n de barra de estado en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto de [CStatusBar](../mfc/reference/cstatusbar-class.md) es una barra de controles con una fila de paneles de resultados de texto.  Los paneles de salida se utilizan como líneas de mensajes como indicadores de estado.  Los ejemplos incluyen las líneas de AYUDA\- mensaje de menú que explican brevemente el comando de menú seleccionado y los indicadores que muestran el estado de BLOQ DESPL, de BLOQ NUM, y otras claves.  
  
 A partir de la versión 4.0 de MFC, barras de estado se implementan mediante la clase [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), que encapsula un control común de barra de estado.  Por compatibilidad con versiones anteriores, MFC conserva la más antigua implementación de barra de estado en la clase **COldStatusBar**.  La documentación para versiones anteriores de MFC describe **COldStatusBar** en `CStatusBar`.  
  
 [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md), una función miembro nueva a MFC 4,0, permite aprovechar las ventajas de la compatibilidad de controles comunes de Windows para la personalización y la funcionalidad adicional de la barra de estado.  las funciones miembro de`CStatusBar` ofrecen la mayor parte de la funcionalidad de los controles comunes de Windows; sin embargo, cuando se llama a `GetStatusBarCtrl`, puede proporcionar a barras de estado aun más de las características de una barra de estado.  Cuando se llama a `GetStatusBarCtrl`, devolverá una referencia a un objeto de `CStatusBarCtrl` .  Puede utilizar esa referencia para manipular el control de barra de estado.  
  
 La ilustración siguiente se muestra una barra de estado que muestra varios marcadores.  
  
 ![Barra de estado](../mfc/media/vc37dy1.png "vc37DY1")  
Una barra de estado  
  
 Como la barra de herramientas, el objeto de la barra de estado se inserta en la ventana de marco principal y se crea automáticamente cuando se construye la ventana de marco.  La barra de estado, como todas las barras de controles, se destruye automáticamente también cuando se destruye el cuadro primario.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Actualizar el texto de un panel de barra de estado](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   Clases MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) y [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [Barras de controles](../mfc/control-bars.md)  
  
-   [Barras de cuadro de diálogo](../mfc/dialog-bars.md)  
  
-   [Barras de herramientas \(implementación de barra de herramientas de MFC\)](../mfc/mfc-toolbar-implementation.md)  
  
## Vea también  
 [Barras de estado](../mfc/status-bars.md)
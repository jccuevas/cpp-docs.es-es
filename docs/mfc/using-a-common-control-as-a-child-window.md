---
title: "Usar un control com&#250;n como ventana secundaria | Microsoft Docs"
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
  - "ventanas secundarias, como controles comunes"
  - "controles comunes [C++], ventanas secundarias"
  - "controles [MFC], utilizar como ventanas secundarias"
  - "ventanas [C++], como controles comunes"
  - "controles comunes de Windows [C++], ventanas secundarias"
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar un control com&#250;n como ventana secundaria
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles comunes cualquiera de Windows se pueden utilizar como una ventana secundaria de cualquier otra ventana.  El procedimiento siguiente describe cómo crear un control común dinámicamente y trabajar con él.  
  
### Para utilizar un control común como una ventana secundaria  
  
1.  Defina el control en la clase o el controlador relacionada.  
  
2.  Override de control del método de [CWnd::Create](../Topic/CWnd::Create.md) para crear el control de Windows.  
  
3.  Una vez creado el control \(ya desde el controlador de `OnCreate` si crea subclases el control\), se puede manipular el control mediante sus funciones miembro.  Vea las descripciones de controles individuales en [Controles](../mfc/controls-mfc.md) para los detalles en métodos.  
  
4.  Cuando termine con el control, utilice [CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md) de destruir el control.  
  
## Vea también  
 [Crear y usar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)
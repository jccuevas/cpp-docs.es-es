---
title: "Estilos de ventana de marco (C++) | Microsoft Docs"
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
  - "ventanas de marco [C++], estilos"
  - "MFC [C++], ventanas de marco"
  - "PreCreateWindow (método), establecer estilos de ventana"
  - "estilos, ventanas"
  - "estilos de ventanas [C++]"
  - "ventanas [C++], MFC"
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de ventana de marco (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las ventanas de marco que se obtiene con el marco son adecuados para la mayoría de los programas, pero puede hacerse flexibilidad adicional utilizando las funciones avanzadas [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) y la función global [Clase](../Topic/AfxRegisterWndClass.md)MFC.  `PreCreateWindow` es una función miembro de `CWnd`.  
  
 Si aplica los estilos de **WS\_HSCROLL** y de **WS\_VSCROLL** a la ventana de marco principal, en su lugar se aplican a la ventana de **MDICLIENT** para que los usuarios puedan desplazarse el área de **MDICLIENT** .  
  
 Si se establece el bit de estilo de **FWS\_ADDTOTITLE** de la ventana \(que es de forma predeterminada\), la vista indica a ventana cuadro qué título a mostrar en la barra de título de la ventana basándose en el nombre de la vista.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Administrar las ventanas secundarias MDI \(MDICLIENT\)](../mfc/managing-mdi-child-windows.md), la ventana dentro de un marco MDI que contiene las ventanas MDI secundarias  
  
-   [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Estilos de ventana](../mfc/reference/window-styles.md)  
  
## Vea también  
 [Ventanas de marco](../mfc/frame-windows.md)
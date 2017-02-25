---
title: "Clases de ventanas de ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, ventanas"
  - "creación de subclases de clases de ventanas ATL"
  - "creación de superclases"
  - "creación de superclases, ATL"
  - "ventanas [C++], ATL"
  - "ventanas [C++], creación de subclases"
  - "ventanas [C++], creación de superclases"
ms.assetid: 1d12b708-de3e-49d5-9e41-42fe4769fa62
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de ventanas de ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL incluye varias clases que le permiten utilizar y que implemente las ventanas.  Estas clases, como otras clases ATL, proporcionan una implementación eficaz que no aplicar una sobrecarga en el código.  
  
 Esta sección describe las clases de ventana ATL y explica cómo utilizarlas.  
  
## En esta sección  
 [Introducción a las clases de ventana ATL](../atl/introduction-to-atl-window-classes.md)  
 Describe brevemente cada clase de ventana ATL y proporciona vínculos al material de referencia en ellos.  
  
 [Mediante una ventana](../atl/using-a-window.md)  
 Explica cómo utilizar `CWindow` manipular una ventana.  
  
 [Implementar una ventana](../atl/implementing-a-window.md)  
 Describe los controladores de mensajes, los mapas de mensajes, y utilizar `CWindowImpl`.  Incluye los detalles en crear superclase y crear subclases.  
  
 [implementar un cuadro de diálogo](../atl/implementing-a-dialog-box.md)  
 Describe los dos métodos para agregar una clase de cuadro de diálogo y se muestra un ejemplo de código.  
  
 [Mediante Windows contenido](../atl/using-contained-windows.md)  
 Comenta contiene estas ventanas en ATL, que son ventanas que delegan sus mensajes a un objeto contenedor en lugar de administrarlos en su propia clase.  
  
 [Rasgos de la ventana](../atl/understanding-window-traits.md)  
 Describe clases de con los de la ventana en ATL.  Estas clases proporcionan un método sencillo para normalizar los estilos utilizados para la creación de un objeto de la ventana.  
  
## Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas conceptuales sobre cómo programar utilizando Active Template Library.  
  
 [Clases de soporte de Windows](../atl/windows-support-classes.md)  
 Enumera las clases adicionales ATL compatibles con ventanas y los mapas de mensajes en ATL.
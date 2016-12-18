---
title: "Administraci&#243;n de memoria | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "memoria"
  - "asignación de memoria"
  - "asignación de memoria, MFC"
  - "memoria, administrar"
  - "MFC, administración de memoria"
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Administraci&#243;n de memoria
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este grupo de casos describe cómo aprovechar los servicios de uso general de la biblioteca Microsoft Foundation Class \(MFC\) relacionada con la administración de memoria.  La asignación de memoria se puede dividir en dos categorías principales: asignaciones de marco y asignaciones de la pila.  
  
 La principal diferencia entre las dos técnicas de asignación es que con la asignación de cuadro trabaja normalmente con el bloque de memoria real propio, mientras que con la asignación de pila proporcionan siempre un puntero al bloque de memoria.  Otra diferencia importante entre los dos esquemas es que los objetos de cuadro automáticamente se eliminarán, mientras que los objetos del montón se deben eliminar explícitamente por el programador.  
  
 Para obtener información de no MFC sobre administración de memoria en programas para Windows, vea [Administración de memoria](http://msdn.microsoft.com/library/windows/desktop/aa366779) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Asignación frame](../mfc/memory-management-frame-allocation.md)  
  
-   [Asignación de pila](../mfc/memory-management-heap-allocation.md)  
  
-   [Asignar memoria para una matriz](../mfc/memory-management-examples.md)  
  
-   [La desasignación de memoria para una matriz de pila](../mfc/memory-management-examples.md)  
  
-   [Asignar memoria para una estructura de datos](../mfc/memory-management-examples.md)  
  
-   [Asignar memoria para un objeto](../mfc/memory-management-examples.md)  
  
-   [Bloques de memoria puede](../mfc/memory-management-resizable-memory-blocks.md)  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)
---
title: "Clases de excepciones y depuraci&#243;n | Microsoft Docs"
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
  - "vc.classes.debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "depurar [MFC], clases para la depuración"
  - "depurar [MFC], clases de excepciones"
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de excepciones y depuraci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases proporcionan compatibilidad para depurar la asignación de memoria dinámica y pasar la información de excepción de la función donde se produce la excepción a la función donde se detecta.  
  
 Utilice las clases [CDumpContext](../mfc/reference/cdumpcontext-class.md) y [CMemoryState](../mfc/reference/cmemorystate-structure.md) durante el desarrollo para ayudar en la depuración, como se describe en [Aplicaciones MFC de depuración](../Topic/MFC%20Debugging%20Techniques.md).  Utilice [Recursos](../mfc/reference/cruntimeclass-structure.md) para determinar el tipo de cualquier objeto en tiempo de ejecución, como se describe en el artículo [Información de acceso de la clase en tiempo de ejecución](../mfc/accessing-run-time-class-information.md).  El marco de trabajo usa `CRuntimeClass` para crear objetos de una clase determinada dinámicamente.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)
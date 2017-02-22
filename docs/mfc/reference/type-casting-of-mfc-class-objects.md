---
title: "Conversi&#243;n de tipos de objetos de clase de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "convertir tipos"
  - "macros, convertir punteros"
  - "macros, convertir tipos"
  - "punteros, convertir tipos"
  - "conversiones de tipos"
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Conversi&#243;n de tipos de objetos de clase de MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las macros de conversión de tipos proporcionan una manera de convertir un puntero determinado a un puntero que señala a un objeto de la clase específica, con o sin comprobar que la conversión es válido.  
  
 La tabla siguiente muestra las macros de conversión de tipos de MFC.  
  
### Punteros de la conversión a de las macros a objetos de la clase MFC  
  
|||  
|-|-|  
|[DYNAMIC\_DOWNCAST](../Topic/DYNAMIC_DOWNCAST.md)|Convierte un puntero a un puntero a un objeto de clase mientras comprueba si la conversión es válido.|  
|[STATIC\_DOWNCAST](../Topic/STATIC_DOWNCAST.md)|Convierte un puntero a un objeto de una clase a un puntero de un tipo relacionado.  En una compilación de depuración, hace **ASERCIÓN** si el objeto no es una “clase” del tipo de destino.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
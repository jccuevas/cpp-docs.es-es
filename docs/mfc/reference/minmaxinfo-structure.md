---
title: "MINMAXINFO (Estructura) | Microsoft Docs"
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
  - "MINMAXINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MINMAXINFO (estructura)"
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MINMAXINFO (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `MINMAXINFO` contiene información sobre el tamaño de una ventana y posición maximizada y su tamaño de visualización mínimo y máximo.  
  
## Sintaxis  
  
```  
  
      typedef struct tagMINMAXINFO {  
   POINT ptReserved;  
   POINT ptMaxSize;  
   POINT ptMaxPosition;  
   POINT ptMinTrackSize;  
   POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### Parámetros  
 *ptReserved*  
 Reservado para uso interno.  
  
 *ptMaxSize*  
 Especifica el ancho maximizado \(point.x\) y el alto maximizado \(point.y\) de la ventana.  
  
 `ptMaxPosition`  
 Especifica la posición del lado izquierdo de la ventana maximizada \(point.x\) y la posición de la parte superior de la ventana maximizada \(point.y\).  
  
 *ptMinTrackSize*  
 Especifica el ancho mínimo de seguimiento \(point.x\) y el alto que sigue mínimo \(point.y\) de la ventana.  
  
 *ptMaxTrackSize*  
 Especifica el ancho máximo de seguimiento \(point.x\) y el alto que sigue máximo \(point.y\) de la ventana.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../Topic/CWnd::OnGetMinMaxInfo.md)
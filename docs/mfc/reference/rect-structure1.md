---
title: "RECT (Estructura) | Microsoft Docs"
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
  - "LPRECT"
  - "RECT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPRECT (estructura)"
  - "RECT (estructura)"
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RECT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura `RECT` define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.  
  
## Sintaxis  
  
```  
  
      typedef struct tagRECT {   
   LONG left;  
   LONG top;  
   LONG right;  
   LONG bottom;  
} RECT;  
```  
  
## Miembros  
 `left`  
 Especifica la coordenada x de la esquina superior izquierda de un rectángulo.  
  
 `top`  
 Especifica la coordenada y de la esquina superior izquierda de un rectángulo.  
  
 `right`  
 Especifica la coordenada x de la esquina inferior derecha de un rectángulo.  
  
 `bottom`  
 Especifica la coordenada y de la esquina inferior derecha de un rectángulo.  
  
## Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/CPP/rect-structure1_1.cpp)]  
  
## Requisitos  
 **Encabezado:** windef.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)
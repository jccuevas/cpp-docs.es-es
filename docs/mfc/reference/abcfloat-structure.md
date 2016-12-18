---
title: "ABCFLOAT (Estructura) | Microsoft Docs"
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
  - "ABCFLOAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ABCFLOAT (estructura)"
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ABCFLOAT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `ABCFLOAT` contiene los anchos de A, b, y c de un carácter de la fuente.  
  
## Sintaxis  
  
```  
  
      typedef struct _ABCFLOAT { /* abcf */  
   FLOAT abcfA;  
   FLOAT abcfB;  
   FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### Parámetros  
 *abcfA*  
 Especifica el espaciado de Del carácter.  El espaciado de A es la distancia a agregar a la posición actual antes de dibujar el glifo de carácter.  
  
 *abcfB*  
 Especifica el espaciado b de caracteres.  El espaciado b es el ancho de la parte dibujada de glifo de carácter.  
  
 *abcfC*  
 Especifica el espaciado de C de caracteres.  El espaciado de C es la distancia a agregar a la posición actual para proporcionar el espacio en blanco a la derecha del glifo de carácter.  
  
## Comentarios  
 Los anchos de A, b, y c se miden a lo largo de la línea base de la fuente.  El incremento de carácter \(ancho total\) de un carácter es la suma de los espacios de A, b, y c.  La A o el espacio de C puede ser negativo indicar underhangs o proyecciones.  
  
## Requisitos  
 **Encabezado:** wingdi.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)
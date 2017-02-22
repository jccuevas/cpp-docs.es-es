---
title: "ABC (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ABC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "estructura ABC"
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# ABC (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de **ABC** contiene el ancho de un carácter en una fuente TrueType.  
  
## Sintaxis  
  
```  
  
      typedef struct _ABC { /* abc */  
   int abcA;  
   UINT abcB;  
   int abcC;  
} ABC;  
```  
  
#### Parámetros  
 *abcA*  
 Especifica el espaciado de Del carácter.  El espaciado de A es la distancia a agregar a la posición actual antes de dibujar el glifo de carácter.  
  
 *abcB*  
 Especifica el espaciado b de caracteres.  El espaciado b es el ancho de la parte dibujada de glifo de carácter.  
  
 *abcC*  
 Especifica el espaciado de C de caracteres.  El espaciado de C es la distancia a agregar a la posición actual para proporcionar el espacio en blanco a la derecha del glifo de carácter.  
  
## Comentarios  
 El ancho total de un carácter es la suma de los espacios de A, b, y c.  La A o el espacio de C puede ser negativo indicar underhangs o proyecciones.  
  
## Requisitos  
 **Encabezado:** wingdi.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)
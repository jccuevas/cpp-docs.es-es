---
title: "XFORM (Estructura) | Microsoft Docs"
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
  - "XFORM"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "XFORM (estructura)"
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# XFORM (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `XFORM` tiene el siguiente formato:  
  
## Sintaxis  
  
```  
  
      typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## Comentarios  
 La estructura de `XFORM` especifica una transformación de página\- espacio de mundo\- espacio.  Los miembros de **eDx** y de **eDy** especifican los componentes horizontal y vertical de traducción, respectivamente.  La tabla siguiente se muestra cómo se utilizan los otros miembros, dependiendo de la operación:  
  
|Operación|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|Coseno del ángulo de rotación|Seno del ángulo de rotación|Seno negativo en ángulo de rotación|Coseno del ángulo de rotación|  
|**Ajustar la escala**|Componente horizontal de escala|Nothing|Nothing|Componente vertical de escala|  
|**Distorsión**|Nothing|Constante horizontal de la proporcionalidad|Constante vertical de la proporcionalidad|Nothing|  
|**Reflexión**|Componente horizontal de reflexión|Nothing|Nothing|Componente vertical de reflexión|  
  
## Requisitos  
 **Encabezado:** wingdi.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../Topic/CRgn::CreateFromData.md)
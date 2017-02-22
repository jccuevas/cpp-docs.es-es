---
title: "CD2DRectF (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DRectF"
  - "CD2DRectF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRectF (clase)"
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DRectF (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un contenedor para `D2D1_RECT_F`.  
  
## Sintaxis  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRectF::CD2DRectF](../Topic/CD2DRectF::CD2DRectF.md)|Sobrecargado.  Construye un objeto de `CD2DRectF` del objeto de `D2D1_RECT_F` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRectF::IsNull](../Topic/CD2DRectF::IsNull.md)|Devuelve un valor de `boolean` que indica si una expresión no contiene datos válido \(`null`\).|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRectF::operator CRect](../Topic/CD2DRectF::operator%20CRect.md)|Convierten `CD2DRectF` al objeto de `CRect` .|  
  
## Jerarquía de herencia  
 `D2D1_RECT_F`  
  
 [CD2DRectF](../../mfc/reference/cd2drectf-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
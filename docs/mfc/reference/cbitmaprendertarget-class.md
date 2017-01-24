---
title: "CBitmapRenderTarget (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CBitmapRenderTarget"
  - "CBitmapRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBitmapRenderTarget (clase)"
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBitmapRenderTarget (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un contenedor para ID2D1BitmapRenderTarget.  
  
## Sintaxis  
  
```  
class CBitmapRenderTarget : public CRenderTarget;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::CBitmapRenderTarget](../Topic/CBitmapRenderTarget::CBitmapRenderTarget.md)|Construye un objeto CBitmapRenderTarget.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::Attach](../Topic/CBitmapRenderTarget::Attach.md)|Adjunta la interfaz de destino de representación existente al objeto|  
|[CBitmapRenderTarget::Detach](../Topic/CBitmapRenderTarget::Detach.md)|Desasocia la interfaz de destino de representación del objeto|  
|[CBitmapRenderTarget::GetBitmap](../Topic/CBitmapRenderTarget::GetBitmap.md)|Recupera el mapa de bits para este destino de representación.  El mapa de bits devuelto se puede utilizar para operaciones de dibujo.|  
|[CBitmapRenderTarget::GetBitmapRenderTarget](../Topic/CBitmapRenderTarget::GetBitmapRenderTarget.md)|Devuelve la interfaz ID2D1BitmapRenderTarget|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget\*](../Topic/CBitmapRenderTarget::operator%20ID2D1BitmapRenderTarget*.md)|Devuelve la interfaz ID2D1BitmapRenderTarget|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::m\_pBitmapRenderTarget](../Topic/CBitmapRenderTarget::m_pBitmapRenderTarget.md)|Puntero a un objeto ID2D1BitmapRenderTarget.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CBitmapRenderTarget](../../mfc/reference/cbitmaprendertarget-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
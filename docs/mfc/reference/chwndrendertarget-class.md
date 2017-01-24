---
title: "CHwndRenderTarget (Clase) | Microsoft Docs"
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
  - "CHwndRenderTarget"
  - "afxrendertarget/CHwndRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHwndRenderTarget (clase)"
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHwndRenderTarget (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1HwndRenderTarget.  
  
## Sintaxis  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::CHwndRenderTarget](../Topic/CHwndRenderTarget::CHwndRenderTarget.md)|Construye un objeto CHwndRenderTarget de HWND.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::Attach](../Topic/CHwndRenderTarget::Attach.md)|Adjunta la interfaz de destino de representación existente al objeto|  
|[CHwndRenderTarget::CheckWindowState](../Topic/CHwndRenderTarget::CheckWindowState.md)|Indica si el HWND asociado a este destino de representación está oculto.|  
|[CHwndRenderTarget::Create](../Topic/CHwndRenderTarget::Create.md)|Crea un destino de representación asociado a la ventana|  
|[CHwndRenderTarget::Detach](../Topic/CHwndRenderTarget::Detach.md)|Desasocia la interfaz de destino de representación del objeto|  
|[CHwndRenderTarget::GetHwnd](../Topic/CHwndRenderTarget::GetHwnd.md)|Devuelve el HWND asociado a este destino de representación.|  
|[CHwndRenderTarget::GetHwndRenderTarget](../Topic/CHwndRenderTarget::GetHwndRenderTarget.md)|Devuelve la interfaz ID2D1HwndRenderTarget.|  
|[CHwndRenderTarget::ReCreate](../Topic/CHwndRenderTarget::ReCreate.md)|Vuelve a crear un destino de representación asociado a la ventana|  
|[CHwndRenderTarget::Resize](../Topic/CHwndRenderTarget::Resize.md)|Cambia el tamaño del destino de representación para el tamaño de píxel especificado|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget\*](../Topic/CHwndRenderTarget::operator%20ID2D1HwndRenderTarget*.md)|Devuelve la interfaz ID2D1HwndRenderTarget.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::m\_pHwndRenderTarget](../Topic/CHwndRenderTarget::m_pHwndRenderTarget.md)|Puntero a un objeto ID2D1HwndRenderTarget.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
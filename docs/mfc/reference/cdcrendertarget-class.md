---
title: "CDCRenderTarget (Clase) | Microsoft Docs"
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
  - "afxrendertarget/CDCRenderTarget"
  - "CDCRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDCRenderTarget (clase)"
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDCRenderTarget (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1DCRenderTarget.  
  
## Sintaxis  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](../Topic/CDCRenderTarget::CDCRenderTarget.md)|Construye un objeto CDCRenderTarget.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](../Topic/CDCRenderTarget::Attach.md)|Adjunta la interfaz de destino de representación existente al objeto|  
|[CDCRenderTarget::BindDC](../Topic/CDCRenderTarget::BindDC.md)|Enlaza el destino de representación al contexto de dispositivo al que emite comandos de dibujo|  
|[CDCRenderTarget::Create](../Topic/CDCRenderTarget::Create.md)|Crea un CDCRenderTarget.|  
|[CDCRenderTarget::Detach](../Topic/CDCRenderTarget::Detach.md)|Desasocia la interfaz de destino de representación del objeto|  
|[CDCRenderTarget::GetDCRenderTarget](../Topic/CDCRenderTarget::GetDCRenderTarget.md)|Devuelve la interfaz ID2D1DCRenderTarget|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget\*](../Topic/CDCRenderTarget::operator%20ID2D1DCRenderTarget*.md)|Devuelve la interfaz ID2D1DCRenderTarget|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::m\_pDCRenderTarget](../Topic/CDCRenderTarget::m_pDCRenderTarget.md)|Puntero a un objeto ID2D1DCRenderTarget.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
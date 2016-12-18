---
title: "CMFCPreviewCtrlImpl Class | Microsoft Docs"
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
  - "CMFCPreviewCtrlImpl"
  - "afxwin/CMFCPreviewCtrlImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPreviewCtrlImpl class"
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPreviewCtrlImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa una ventana que se coloque en una ventana host proporcionada por el shell para Rich Preview.  
  
## Sintaxis  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl](../Topic/CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl.md)|Destructs un objeto del control de vista previa.|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](../Topic/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl.md)|Construye un objeto del control de vista previa.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](../Topic/CMFCPreviewCtrlImpl::Create.md)|Sobrecargado.  Llama un controlador preview enriquecidas para crear la ventana de Windows.|  
|[CMFCPreviewCtrlImpl::Destroy](../Topic/CMFCPreviewCtrlImpl::Destroy.md)|Llama un controlador preview enriquecidas cuando necesita destruir este control.|  
|[CMFCPreviewCtrlImpl::Focus](../Topic/CMFCPreviewCtrlImpl::Focus.md)|Establece el foco de entrada en este control.|  
|[CMFCPreviewCtrlImpl::GetDocument](../Topic/CMFCPreviewCtrlImpl::GetDocument.md)|Devuelve un documento conectado a este control de vista previa.|  
|[CMFCPreviewCtrlImpl::Redraw](../Topic/CMFCPreviewCtrlImpl::Redraw.md)|indica a este control que actualizar.|  
|[CMFCPreviewCtrlImpl::SetDocument](../Topic/CMFCPreviewCtrlImpl::SetDocument.md)|Invoca el controlador preview para crear una relación entre la aplicación del documento y el control de vista previa.|  
|[CMFCPreviewCtrlImpl::SetHost](../Topic/CMFCPreviewCtrlImpl::SetHost.md)|Establece un nuevo elemento primario de este control.|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](../Topic/CMFCPreviewCtrlImpl::SetPreviewVisuals.md)|Llama un controlador preview enriquecidas cuando necesita establecer representaciones visuales del contenido de la vista previa de amplio.|  
|[CMFCPreviewCtrlImpl::SetRect](../Topic/CMFCPreviewCtrlImpl::SetRect.md)|establece un nuevo rectángulo delimitador para este control.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](../Topic/CMFCPreviewCtrlImpl::DoPaint.md)|Llamado por el marco para representar la vista previa.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m\_clrBackColor](../Topic/CMFCPreviewCtrlImpl::m_clrBackColor.md)|color de fondo de la ventana de vista previa.|  
|[CMFCPreviewCtrlImpl::m\_clrTextColor](../Topic/CMFCPreviewCtrlImpl::m_clrTextColor.md)|Color del texto de la ventana de vista previa.|  
|[CMFCPreviewCtrlImpl::m\_font](../Topic/CMFCPreviewCtrlImpl::m_font.md)|Fuente utilizada para mostrar el texto en la ventana de vista previa.|  
|[CMFCPreviewCtrlImpl::m\_pDocument](../Topic/CMFCPreviewCtrlImpl::m_pDocument.md)|Un puntero a un documento cuyo contenido se obtenga una vista previa del control.|  
  
## Comentarios  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)  
  
## Requisitos  
 **Encabezado:** afxwin.h
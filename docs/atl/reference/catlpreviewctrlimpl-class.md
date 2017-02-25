---
title: "CAtlPreviewCtrlImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "atlpreviewctrlimpl/ATL::CAtlPreviewCtrlImpl"
  - "CAtlPreviewCtrlImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlPreviewCtrlImpl class"
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CAtlPreviewCtrlImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es una implementación de ATL de una ventana que se coloque en una ventana host proporcionada por el shell para la vista previa enriquecidas.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl](../Topic/CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl.md)|Destructs un objeto del control de vista previa.|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](../Topic/CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl.md)|Construye un objeto del control de vista previa.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::Create](../Topic/CAtlPreviewCtrlImpl::Create.md)|Llama un controlador preview enriquecidas para crear la ventana de Windows.|  
|[CAtlPreviewCtrlImpl::Destroy](../Topic/CAtlPreviewCtrlImpl::Destroy.md)|Llama un controlador preview enriquecidas cuando necesita destruir este control.|  
|[CAtlPreviewCtrlImpl::Focus](../Topic/CAtlPreviewCtrlImpl::Focus.md)|Establece el foco de entrada en este control.|  
|[CAtlPreviewCtrlImpl::OnPaint](../Topic/CAtlPreviewCtrlImpl::OnPaint.md)|Controla el mensaje WM\_PAINT.|  
|[CAtlPreviewCtrlImpl::Redraw](../Topic/CAtlPreviewCtrlImpl::Redraw.md)|indica a este control que actualizar.|  
|[CAtlPreviewCtrlImpl::SetHost](../Topic/CAtlPreviewCtrlImpl::SetHost.md)|Establece un nuevo elemento primario de este control.|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](../Topic/CAtlPreviewCtrlImpl::SetPreviewVisuals.md)|Llama un controlador preview enriquecidas cuando necesita establecer representaciones visuales del contenido de la vista previa de amplio.|  
|[CAtlPreviewCtrlImpl::SetRect](../Topic/CAtlPreviewCtrlImpl::SetRect.md)|establece un nuevo rectángulo delimitador para este control.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::DoPaint](../Topic/CAtlPreviewCtrlImpl::DoPaint.md)|Llamado por el marco para representar la vista previa.|  
  
### Constantes protegidas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m\_plf](../Topic/CAtlPreviewCtrlImpl::m_plf.md)|Fuente utilizada para mostrar el texto en la ventana de vista previa.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m\_clrBack](../Topic/CAtlPreviewCtrlImpl::m_clrBack.md)|color de fondo de la ventana de vista previa.|  
|[CAtlPreviewCtrlImpl::m\_clrText](../Topic/CAtlPreviewCtrlImpl::m_clrText.md)|Color del texto de la ventana de vista previa.|  
  
## Comentarios  
  
## Jerarquía de herencia  
 `TBase`  
  
 `ATL::CMessageMap`  
  
 `ATL::CWindowImplRoot<TBase>`  
  
 `ATL::CWindowImplBaseT<TBase,TWinTraits>`  
  
 [ATL::CWindowImpl\<CAtlPreviewCtrlImpl\>](../../atl/reference/cwindowimpl-class.md)  
  
 `IPreviewCtrl`  
  
 `ATL::CAtlPreviewCtrlImpl`  
  
## Requisitos  
 **encabezado:** atlpreviewctrlimpl.h  
  
## Vea también  
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)
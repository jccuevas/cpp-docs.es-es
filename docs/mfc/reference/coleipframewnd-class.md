---
title: "COleIPFrameWnd Class | Microsoft Docs"
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
  - "COleIPFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleIPFrameWnd class"
  - "in-place editing"
  - "OLE, editar"
  - "OLE, in-place activation"
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleIPFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Base para la ventana de la edición en contexto de la aplicación.  
  
## Sintaxis  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](../Topic/COleIPFrameWnd::COleIPFrameWnd.md)|Crea un objeto `COleIPFrameWnd`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](../Topic/COleIPFrameWnd::OnCreateControlBars.md)|Llamado por el marco cuando un elemento se activa para la edición en contexto.|  
|[COleIPFrameWnd::RepositionFrame](../Topic/COleIPFrameWnd::RepositionFrame.md)|Llamado por el marco para colocar la ventana de la edición en contexto de nuevo.|  
  
## Comentarios  
 Esta clase crea y coloca las barras de controles en la ventana de documento de la aplicación contenedora.  También controla las notificaciones generadas por un objeto incrustado de [COleResizeBar](../../mfc/reference/coleresizebar-class.md) cuando el usuario cambia el tamaño de la ventana de la edición en contexto.  
  
 Para obtener más información sobre cómo utilizar `COleIPFrameWnd`, vea el artículo [activación](../../mfc/activation-cpp.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)
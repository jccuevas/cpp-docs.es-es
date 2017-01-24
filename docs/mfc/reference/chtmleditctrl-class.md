---
title: "CHtmlEditCtrl Class | Microsoft Docs"
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
  - "CHtmlEditCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditCtrl class"
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlEditCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.  
  
## Sintaxis  
  
```  
class CHtmlEditCtrl: public CWnd,   
   public CHtmlEditCtrlBase< CHtmlEditCtrl >  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](../Topic/CHtmlEditCtrl::CHtmlEditCtrl.md)|Crea un objeto `CHtmlEditCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](../Topic/CHtmlEditCtrl::Create.md)|Crea un control ActiveX de WebBrowser y lo asocia al objeto de `CHtmlEditCtrl` .  Esta función coloca automáticamente el control ActiveX de WebBrowser en modo de edición.|  
|[CHtmlEditCtrl::GetDHtmlDocument](../Topic/CHtmlEditCtrl::GetDHtmlDocument.md)|Recupera la interfaz de [IHTMLDocument2](https://msdn.microsoft.com/en-us/library/aa752574.aspx) en el documento cargado actualmente en el control contenido WebBrowser.|  
|[CHtmlEditCtrl::GetStartDocument](../Topic/CHtmlEditCtrl::GetStartDocument.md)|Recupera la dirección URL a un documento predeterminado para cargar en el control contenido WebBrowser.|  
  
## Comentarios  
 El control hospedado WebBrowser automáticamente se coloca en modo de edición después de que se cree.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## Requisitos  
 **encabezado:** afxhtml.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
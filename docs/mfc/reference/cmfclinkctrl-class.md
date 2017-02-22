---
title: "CMFCLinkCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCLinkCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCLinkCtrl class"
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCLinkCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Muestra de clase de `CMFCLinkCtrl` un botón como hipervínculo y se invoca el vínculo de destino cuando se hace clic en el botón.  
  
## Sintaxis  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](../Topic/CMFCLinkCtrl::SetURL.md)|Muestra una dirección URL especificada como el texto del botón.|  
|[CMFCLinkCtrl::SetURLPrefix](../Topic/CMFCLinkCtrl::SetURLPrefix.md)|Establece el protocolo implícita \(por ejemplo, “HTTP: "\) de la dirección URL.|  
|[CMFCLinkCtrl::SizeToContent](../Topic/CMFCLinkCtrl::SizeToContent.md)|Cambia el tamaño del botón para contener el texto del botón o el mapa de bits.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](../Topic/CMFCLinkCtrl::OnDrawFocusRect.md)|Llamado por el marco antes del rectángulo de foco de botón se dibuja.|  
  
## Comentarios  
 Cuando se hace clic en un botón que sea derivado de la clase de `CMFCLinkCtrl` , el marco pasa la dirección URL del botón como parámetro al método de `ShellExecute` .  El método de `ShellExecute` abre el destino de la dirección URL.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo establecer el tamaño de un objeto de `CMFCLinkCtrl` , y cómo establecer un URL e información sobre herramientas en un objeto de `CMFCLinkCtrl` .  Este ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/CPP/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/CPP/cmfclinkctrl-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxlinkctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CLinkCtrl Class](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)
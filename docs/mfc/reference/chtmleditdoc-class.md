---
title: "CHtmlEditDoc Class | Microsoft Docs"
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
  - "CHtmlEditDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditDoc class"
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlEditDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Con [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), proporciona la funcionalidad de la plataforma de edición WebBrowser en el contexto de la arquitectura de la vista del documento de MFC.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE CHtmlEditDoc : public CDocument  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditDoc::CHtmlEditDoc](../Topic/CHtmlEditDoc::CHtmlEditDoc.md)|Crea un objeto `CHtmlEditDoc`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditDoc::GetView](../Topic/CHtmlEditDoc::GetView.md)|Recupera el objeto de `CHtmlEditView` asociado a este documento.|  
|[CHtmlEditDoc::IsModified](../Topic/CHtmlEditDoc::IsModified.md)|Devuelve si el control asociado WebBrowser de la vista contiene un documento que ha sido modificado por el usuario.|  
|[CHtmlEditDoc::OpenURL](../Topic/CHtmlEditDoc::OpenURL.md)|Abra una dirección URL.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `CHtmlEditDoc`  
  
## Requisitos  
 **encabezado:** afxhtml.h  
  
## Vea también  
 [Ejemplo HTMLEdit](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
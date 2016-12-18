---
title: "CDocItem Class | Microsoft Docs"
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
  - "CDocItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocItem class"
  - "client document items"
  - "container document items"
  - "document items"
  - "items, documento"
  - "OLE documents, items"
  - "server documents"
  - "server documents, document items"
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base para los elementos de documento, que son componentes de los datos de un documento.  
  
## Sintaxis  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocItem::GetDocument](../Topic/CDocItem::GetDocument.md)|devuelve el documento que contiene el elemento.|  
|[CDocItem::IsBlank](../Topic/CDocItem::IsBlank.md)|determina si el elemento contiene alguna información.|  
  
## Comentarios  
 los objetos de`CDocItem` se utilizan para representar elementos de OLE en documentos de cliente y servidor.  
  
 Para obtener más información, vea el artículo [contenedores: implementar un contenedor](../../mfc/containers-implementing-a-container.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)
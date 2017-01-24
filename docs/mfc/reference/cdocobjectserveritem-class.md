---
title: "CDocObjectServerItem Class | Microsoft Docs"
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
  - "CDocObjectServerItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "CDocObjectServerItem class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocObjectServerItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa verbos de servidor OLE específicamente para los servidores de DocObject.  
  
## Sintaxis  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](../Topic/CDocObjectServerItem::CDocObjectServerItem.md)|Crea un objeto `CDocObjectServerItem`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](../Topic/CDocObjectServerItem::GetDocument.md)|Recupera un puntero al documento que contiene el elemento.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](../Topic/CDocObjectServerItem::OnHide.md)|Produce una excepción si los intentos de marco para ocultar un elemento de DocObject.|  
|[CDocObjectServerItem::OnShow](../Topic/CDocObjectServerItem::OnShow.md)|Llamado por el marco para crear el elemento de DocObject el activo en contexto.  Si el elemento no es un DocObject, llama a [COleServerItem::OnShow](../Topic/COleServerItem::OnShow.md).|  
  
## Comentarios  
 `CDocObjectServerItem` define funciones overridable miembro: [OnHide](../Topic/CDocObjectServerItem::OnHide.md), [OnOpen](http://msdn.microsoft.com/es-es/7a9b1363-6ad8-4732-9959-4e35c07644fd), y [OnShow](../Topic/CDocObjectServerItem::OnShow.md).  
  
 Para utilizar `CDocObjectServerItem`, garantizar que la invalidación de [OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) en su `COleServerDoc`\- clase derivada devuelve un nuevo objeto de `CDocObjectServerItem` .  Si necesita cambiar alguna funcionalidad en el elemento, puede crear una nueva instancia de su propio `CDocObjectServerItem`\- clase derivada.  
  
 Para obtener más información sobre DocObjects, vea [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en *la referencia de MFC*.  Vea también [Primeros pasos de internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## Requisitos  
 **Header:** afxdocob.h  
  
## Vea también  
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer Class](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem Class](../../mfc/reference/coledocobjectitem-class.md)
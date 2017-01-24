---
title: "CDocObjectServer Class | Microsoft Docs"
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
  - "CDocObjectServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "CDocObjectServer class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocObjectServer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa las interfaces VIEJAS adicionales necesarias para crear un servidor normal de `COleDocument` en un servidor completo de DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, y `IPrint`.  
  
## Sintaxis  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::CDocObjectServer](../Topic/CDocObjectServer::CDocObjectServer.md)|Crea un objeto `CDocObjectServer`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::ActivateDocObject](../Topic/CDocObjectServer::ActivateDocObject.md)|Activa el servidor del objeto document, pero no lo muestra.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](../Topic/CDocObjectServer::OnActivateView.md)|Muestra la vista de DocObject.|  
|[CDocObjectServer::OnApplyViewState](../Topic/CDocObjectServer::OnApplyViewState.md)|Restaura el estado de vista DocObject.|  
|[CDocObjectServer::OnSaveViewState](../Topic/CDocObjectServer::OnSaveViewState.md)|Guarda el estado de vista DocObject.|  
  
## Comentarios  
 `CDocObjectServer` se deriva de `CCmdTarget` y trabajos de mediante un `COleServerDoc` para exponer las interfaces.  
  
 Un documento de servidor de DocObject puede contener objetos de [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) , que representan la interfaz del servidor a los elementos de DocObject.  
  
 Para personalizar su servidor de DocObject, derive su propia clase de `CDocObjectServer` y reemplazar la configuración de vista funciona, [OnActivateView](../Topic/CDocObjectServer::OnActivateView.md), [OnApplyViewState](../Topic/CDocObjectServer::OnApplyViewState.md), y [OnSaveViewState](../Topic/CDocObjectServer::OnSaveViewState.md).  Necesitará proporcionar una nueva instancia de la clase en respuesta a llamadas del marco.  
  
 Para obtener más información sobre DocObjects, vea [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en *la referencia de MFC*.  Vea también [Primeros pasos de internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
 También vea el siguiente artículo de Knowledge Base:  
  
-   Q247382: PRB: Información sobre herramientas para los Controles del Servidor De documento ActiveX oculto por el contenedor de documento ActiveX  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## Requisitos  
 **Header:** afxdocob.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem Class](../../mfc/reference/cdocobjectserveritem-class.md)
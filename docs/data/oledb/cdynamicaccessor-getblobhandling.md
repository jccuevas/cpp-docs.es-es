---
title: "CDynamicAccessor::GetBlobHandling | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDynamicAccessor.GetBlobHandling"
  - "CDynamicAccessor::GetBlobHandling"
  - "ATL::CDynamicAccessor::GetBlobHandling"
  - "GetBlobHandling"
  - "CDynamicAccessor.GetBlobHandling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBlobHandling (método)"
ms.assetid: bbc6dda6-e132-42a3-980d-24e455cbe456
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetBlobHandling
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera BLOB que administra el valor de la fila actual.  
  
## Sintaxis  
  
```  
  
const DBBLOBHANDLINGENUM GetBlobHandling( ) const;  
  
```  
  
## Comentarios  
 Devuelve BLOB que administra el valor `eBlobHandling` como lo establece [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)
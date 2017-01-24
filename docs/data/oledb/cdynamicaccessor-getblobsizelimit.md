---
title: "CDynamicAccessor::GetBlobSizeLimit | Microsoft Docs"
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
  - "ATL::CDynamicAccessor::GetBlobSizeLimit"
  - "CDynamicAccessor.GetBlobSizeLimit"
  - "CDynamicAccessor::GetBlobSizeLimit"
  - "GetBlobSizeLimit"
  - "ATL.CDynamicAccessor.GetBlobSizeLimit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBlobSizeLimit (método)"
ms.assetid: 7131e7c4-6e05-42f3-9d87-110301b672f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetBlobSizeLimit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el tamaño máximo del BLOB en bytes.  
  
## Sintaxis  
  
```  
  
const DBLENGTH GetBlobSizeLimit( ) const;  
  
```  
  
## Comentarios  
 Devuelve BLOB que administra el valor `nBlobSize` como lo establece [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)
---
title: "CBulkRowset::SetRows | Microsoft Docs"
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
  - "ATL.CBulkRowset.SetRows"
  - "CBulkRowset::SetRows"
  - "CBulkRowset<TAccessor>.SetRows"
  - "ATL.CBulkRowset<TAccessor>.SetRows"
  - "CBulkRowset<TAccessor>::SetRows"
  - "ATL::CBulkRowset<TAccessor>::SetRows"
  - "ATL::CBulkRowset::SetRows"
  - "CBulkRowset.SetRows"
  - "SetRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetRows (método)"
ms.assetid: 7e92312a-bfd0-4c24-a799-62bef663f28e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBulkRowset::SetRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el número de identificadores de fila recuperados por cada llamada.  
  
## Sintaxis  
  
```  
  
      void SetRows(  
   DBROWCOUNT nRows   
) throw( );  
```  
  
#### Parámetros  
 `nRows`  
 \[in\] El nuevo tamaño de conjunto de filas \(número de filas\).  
  
## Comentarios  
 Si se llama a esta función, debe ser antes de que abra el conjunto de filas.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CBulkRowset \(Clase\)](../../data/oledb/cbulkrowset-class.md)
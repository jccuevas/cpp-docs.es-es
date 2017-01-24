---
title: "IRowsetChangeImpl::DeleteRows | Microsoft Docs"
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
  - "ATL.IRowsetChangeImpl.DeleteRows"
  - "ATL::IRowsetChangeImpl::DeleteRows"
  - "IRowsetChangeImpl.DeleteRows"
  - "DeleteRows"
  - "IRowsetChangeImpl::DeleteRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DeleteRows (método)"
ms.assetid: 462ad4f1-3b2a-4134-9733-be65708aa1d9
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetChangeImpl::DeleteRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Elimina filas del conjunto de filas.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( DeleteRows )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWSTATUS rgRowStatus[]   
);  
```  
  
#### Parámetros  
 Vea [IRowsetChange::DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetChangeImpl \(Clase\)](../../data/oledb/irowsetchangeimpl-class.md)
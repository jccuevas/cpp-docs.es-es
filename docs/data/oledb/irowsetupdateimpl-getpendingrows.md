---
title: "IRowsetUpdateImpl::GetPendingRows | Microsoft Docs"
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
  - "IRowsetUpdateImpl::GetPendingRows"
  - "GetPendingRows"
  - "IRowsetUpdateImpl.GetPendingRows"
  - "ATL::IRowsetUpdateImpl::GetPendingRows"
  - "ATL.IRowsetUpdateImpl.GetPendingRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPendingRows (método)"
ms.assetid: 2d1ef748-da6d-4184-98dc-096427358dfd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::GetPendingRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve una lista de filas con cambios pendientes.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( GetPendingRows )(  
   HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus   
);  
```  
  
#### Parámetros  
 `hReserved`  
 \[in\] Corresponde a `hChapter` el parámetro en [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx).  
  
 Para otros parámetros, vea [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Para obtener más información, vea [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetUpdateImpl \(Clase\)](../../data/oledb/irowsetupdateimpl-class.md)
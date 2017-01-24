---
title: "IRowsetImpl::RefRows | Microsoft Docs"
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
  - "ATL::IRowsetImpl::RefRows"
  - "ATL.IRowsetImpl.RefRows"
  - "IRowsetImpl.RefRows"
  - "RefRows"
  - "IRowsetImpl::RefRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RefRows (método)"
ms.assetid: 1c048a2a-65dc-4bba-9c81-a23c0dc249c8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::RefRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llamado por [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) o el incremento o liberar un recuento de referencias en un identificador de fila existente.  
  
## Sintaxis  
  
```  
  
      HRESULT RefRows(  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd   
);  
```  
  
#### Parámetros  
 Vea [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 Un valor estándar de `HRESULT` .  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)   
 [CSimpleRow \(Clase\)](../../data/oledb/csimplerow-class.md)
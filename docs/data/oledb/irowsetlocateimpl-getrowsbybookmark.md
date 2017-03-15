---
title: "IRowsetLocateImpl::GetRowsByBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetLocateImpl::GetRowsByBookmark"
  - "IRowsetLocateImpl.GetRowsByBookmark"
  - "GetRowsByBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowsByBookmark (método)"
ms.assetid: 07906e42-3582-427e-812a-aa19791e3c56
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetLocateImpl::GetRowsByBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Captura una o más filas que coinciden con los marcadores especificados.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( GetRowsByBookmark )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]   
);  
```  
  
#### Parámetros  
 `hReserved`  
 \[in\] Corresponde a `hChapter` parámetro a [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx).  
  
 Para otros parámetros, vea [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx) en *la referencia del*programador.  
  
## Comentarios  
 El marcador puede ser un valor que se define o OLE DB [marcadores estándar](https://msdn.microsoft.com/en-us/library/ms712954.aspx) \(**DBBMK\_FIRST** o **DBBMK\_LAST**\).  No cambia la posición del cursor.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetLocateImpl \(Clase\)](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)
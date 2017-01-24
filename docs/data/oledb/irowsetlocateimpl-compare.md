---
title: "IRowsetLocateImpl::Compare | Microsoft Docs"
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
  - "ATL.IRowsetLocateImpl.Compare"
  - "IRowsetLocateImpl::Compare"
  - "IRowsetLocateImpl.Compare"
  - "ATL::IRowsetLocateImpl::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Compare (método)"
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetLocateImpl::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara dos marcadores.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( Compare )(  
   HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison   
);  
```  
  
#### Parámetros  
 Vea [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Cualquiera de los marcadores puede ser OLE estándar [marcador estándar](https://msdn.microsoft.com/en-us/library/ms712954.aspx) DB\-definido \(**DBBMK\_FIRST**, **DBBMK\_LAST**, o **DBBMK\_INVALID**\).  El valor devuelto en `pComparison` indica la relación entre los dos marcadores:  
  
-   **DBCOMPARE\_LT** \(`cbBookmark1` es antes de `cbBookmark2`.\)  
  
-   **DBCOMPARE\_EQ** \(`cbBookmark1` es igual a `cbBookmark2`.\)  
  
-   **DBCOMPARE\_GT** \(`cbBookmark1` es después de `cbBookmark2`.\)  
  
-   **DBCOMPARE\_NE** \(marcadores de The son iguales y no ordenados.\)  
  
-   **DBCOMPARE\_NOTCOMPARABLE** \(marcadores de no se pueden comparar.\)  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetLocateImpl \(Clase\)](../../data/oledb/irowsetlocateimpl-class.md)
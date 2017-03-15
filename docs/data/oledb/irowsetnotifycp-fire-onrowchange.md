---
title: "IRowsetNotifyCP::Fire_OnRowChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyCP.Fire_OnRowChange"
  - "ATL.IRowsetNotifyCP.Fire_OnRowChange"
  - "Fire_OnRowChange"
  - "ATL::IRowsetNotifyCP::Fire_OnRowChange"
  - "IRowsetNotifyCP::Fire_OnRowChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Fire_OnRowChange (método)"
ms.assetid: 6f9beed6-7a69-4c92-936f-422e98f3de5c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetNotifyCP::Fire_OnRowChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Propaga un evento de [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) a todos los agentes de escucha del punto de conexión **IID\_IRowsetNotify** para notificar a los consumidores de un cambio que afecta a las filas.  
  
## Sintaxis  
  
```  
  
      HRESULT Fire_OnRowChange(  
   IRowset* pRowset,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny   
);  
```  
  
#### Parámetros  
 Vea [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetNotifyCP \(Clase\)](../../data/oledb/irowsetnotifycp-class.md)
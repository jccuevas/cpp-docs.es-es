---
title: "IRowsetNotifyCP::Fire_OnRowsetChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Fire_OnRowsetChange"
  - "IRowsetNotifyCP::Fire_OnRowsetChange"
  - "IRowsetNotifyCP.Fire_OnRowsetChange"
  - "ATL::IRowsetNotifyCP::Fire_OnRowsetChange"
  - "ATL.IRowsetNotifyCP.Fire_OnRowsetChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Fire_OnRowsetChange (método)"
ms.assetid: 412a9ec2-5041-4c56-acda-dc8f8e9b35f3
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetNotifyCP::Fire_OnRowsetChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Propaga un evento de [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) a todos los agentes de escucha del punto de conexión **IID\_IRowsetNotify** para notificar a los consumidores de un cambio que afecta al conjunto de filas completo.  
  
## Sintaxis  
  
```  
  
      HRESULT Fire_OnRowsetChange(  
   IRowset* pRowset,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny   
);  
```  
  
#### Parámetros  
 Vea [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetNotifyCP \(Clase\)](../../data/oledb/irowsetnotifycp-class.md)
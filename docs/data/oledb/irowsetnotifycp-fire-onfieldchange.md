---
title: "IRowsetNotifyCP::Fire_OnFieldChange | Microsoft Docs"
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
  - "Fire_OnFieldChange"
  - "ATL::IRowsetNotifyCP::Fire_OnFieldChange"
  - "ATL.IRowsetNotifyCP.Fire_OnFieldChange"
  - "IRowsetNotifyCP.Fire_OnFieldChange"
  - "IRowsetNotifyCP::Fire_OnFieldChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Fire_OnFieldChange (método)"
ms.assetid: 03dad058-8d4f-4113-aea4-ef7764eab9ec
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetNotifyCP::Fire_OnFieldChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Propaga un evento de [OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) para notificar a los consumidores de un cambio del valor de una columna.  
  
## Sintaxis  
  
```  
  
      HRESULT Fire_OnFieldChange(  
   IRowset* pRowset,  
   HROW hRow,  
   DBORDINAL cColumns,  
   DBORDINAL* rgColumns,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny   
);  
```  
  
#### Parámetros  
 Vea [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetNotifyCP \(Clase\)](../../data/oledb/irowsetnotifycp-class.md)
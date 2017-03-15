---
title: "IErrorRecordsImpl::GetCustomErrorObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IErrorRecordsImpl::GetCustomErrorObject"
  - "IErrorRecordsImpl::GetCustomErrorObject"
  - "ATL.IErrorRecordsImpl.GetCustomErrorObject"
  - "IErrorRecordsImpl.GetCustomErrorObject"
  - "GetCustomErrorObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCustomErrorObject (método)"
ms.assetid: 96d3549b-a49c-4552-94b2-71babaf1bf20
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IErrorRecordsImpl::GetCustomErrorObject
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero a una interfaz en un objeto de error personalizado.  
  
## Sintaxis  
  
```  
  
      STDMETHOD( GetCustomErrorObject )(  
   ULONG ulRecordNum,  
   REFIID riid,  
   IUnknown **ppObject   
);  
```  
  
#### Parámetros  
 Vea [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IErrorRecordsImpl \(Clase\)](../../data/oledb/ierrorrecordsimpl-class.md)
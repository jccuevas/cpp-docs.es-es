---
title: "IErrorRecordsImpl::GetBasicErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IErrorRecordsImpl::GetBasicErrorInfo"
  - "IErrorRecordsImpl::GetBasicErrorInfo"
  - "GetBasicErrorInfo"
  - "ATL.IErrorRecordsImpl.GetBasicErrorInfo"
  - "IErrorRecordsImpl.GetBasicErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBasicErrorInfo (método)"
ms.assetid: d0b4dec3-f32a-4aaa-8365-524f2e7c8395
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IErrorRecordsImpl::GetBasicErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve información básica sobre el error, como el código devuelto y el número de error proveedor\- concreto.  
  
## Sintaxis  
  
```  
  
      STDMETHOD( GetBasicErrorInfo )(  
   ULONG ulRecordNum,  
   ERRORINFO *pErrorInfo   
);  
```  
  
#### Parámetros  
 Vea [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IErrorRecordsImpl \(Clase\)](../../data/oledb/ierrorrecordsimpl-class.md)
---
title: "IErrorRecordsImpl::GetErrorGUID | Microsoft Docs"
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
  - "GetErrorGUID"
  - "IErrorRecordsImpl.GetErrorGUID"
  - "IErrorRecordsImpl::GetErrorGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorGUID (método)"
ms.assetid: 42c00755-50e5-401a-8246-adef9de5ced2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el error GUID de un registro de errores.  
  
## Sintaxis  
  
```  
  
      REFGUID GetErrorGUID(  
   ERRORINFO& rCurError   
);  
```  
  
#### Parámetros  
 `rCurError`  
 Un registro de `ERRORINFO` en una interfaz de **IErrorInfo** .  
  
## Valor devuelto  
 Una referencia al GUID para el error.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IErrorRecordsImpl \(Clase\)](../../data/oledb/ierrorrecordsimpl-class.md)
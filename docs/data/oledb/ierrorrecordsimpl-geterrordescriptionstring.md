---
title: "IErrorRecordsImpl::GetErrorDescriptionString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetErrorDescriptionString"
  - "IErrorRecordsImpl.GetErrorDescriptionString"
  - "IErrorRecordsImpl::GetErrorDescriptionString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorDescriptionString (método)"
ms.assetid: 8bc71c45-ca9f-4632-bb02-1aa9ed8086c4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IErrorRecordsImpl::GetErrorDescriptionString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la cadena de descripción del error de un registro de errores.  
  
## Sintaxis  
  
```  
  
      LPOLESTR GetErrorDescriptionString(  
   ERRORINFO& rCurError   
);  
```  
  
#### Parámetros  
 `rCurError`  
 Un registro de `ERRORINFO` en una interfaz de **IErrorInfo** .  
  
## Valor devuelto  
 Un puntero a una cadena que describe el error.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IErrorRecordsImpl \(Clase\)](../../data/oledb/ierrorrecordsimpl-class.md)
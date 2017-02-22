---
title: "CDBErrorInfo::GetErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetErrorInfo"
  - "ATL.CDBErrorInfo.GetErrorInfo"
  - "CDBErrorInfo.GetErrorInfo"
  - "ATL::CDBErrorInfo::GetErrorInfo"
  - "CDBErrorInfo::GetErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorInfo (método)"
ms.assetid: 234e1f02-c307-4666-b3ce-2a4d62407fa1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDBErrorInfo::GetErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llama a [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) para devolver un puntero de interfaz de [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) el registro especificado.  
  
## Sintaxis  
  
```  
  
      HRESULT GetErrorInfo(   
   ULONG ulRecordNum,   
   LCID lcid,   
   IErrorInfo** ppErrorInfo    
) const throw( );  
```  
  
#### Parámetros  
 Vea [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBErrorInfo \(Clase\)](../../data/oledb/cdberrorinfo-class.md)
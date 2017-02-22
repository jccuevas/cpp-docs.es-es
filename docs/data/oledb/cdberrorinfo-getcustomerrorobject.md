---
title: "CDBErrorInfo::GetCustomErrorObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBErrorInfo::GetCustomErrorObject"
  - "ATL.CDBErrorInfo.GetCustomErrorObject"
  - "CDBErrorInfo.GetCustomErrorObject"
  - "ATL::CDBErrorInfo::GetCustomErrorObject"
  - "GetCustomErrorObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCustomErrorObject (método)"
ms.assetid: 295c053c-b76c-47a5-adfb-333e65d2df0d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDBErrorInfo::GetCustomErrorObject
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llama a [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) para devolver un puntero a una interfaz en un objeto de error personalizado.  
  
## Sintaxis  
  
```  
  
      HRESULT GetCustomErrorObject(   
   ULONG ulRecordNum,   
   REFIID riid,   
   IUnknown** ppObject    
) const throw( );  
```  
  
#### Parámetros  
 Vea [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBErrorInfo \(Clase\)](../../data/oledb/cdberrorinfo-class.md)
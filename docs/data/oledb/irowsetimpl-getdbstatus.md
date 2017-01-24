---
title: "IRowsetImpl::GetDBStatus | Microsoft Docs"
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
  - "GetDBStatus"
  - "IRowsetImpl.GetDBStatus"
  - "IRowsetImpl::GetDBStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDBStatus (método)"
ms.assetid: e51d8ee2-fc0c-4909-861c-026c94fb0dfc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::GetDBStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve los indicadores de estado de `DBSTATUS` para el campo especificado.  
  
## Sintaxis  
  
```  
  
      virtual DBSTATUS GetDBStatus(  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames   
);  
```  
  
#### Parámetros  
 \[in\] `currentRow`  
 La fila actual.  
  
 \[in\] `columnNames`  
 La columna para la que solicitan el estado.  
  
## Valor devuelto  
 Los marcadores de [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) para la columna.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)
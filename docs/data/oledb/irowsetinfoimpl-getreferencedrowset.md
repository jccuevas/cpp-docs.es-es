---
title: "IRowsetInfoImpl::GetReferencedRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetInfoImpl::GetReferencedRowset"
  - "GetReferencedRowset"
  - "ATL.IRowsetInfoImpl.GetReferencedRowset"
  - "IRowsetInfoImpl.GetReferencedRowset"
  - "IRowsetInfoImpl::GetReferencedRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetReferencedRowset (método)"
ms.assetid: 94d2155c-9da0-4c19-a37c-bc35716359fd
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetInfoImpl::GetReferencedRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero de interfaz al conjunto de filas al que el marcador aplica.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( GetReferencedRowset )(  
   DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset   
);  
```  
  
#### Parámetros  
 Vea [IRowsetInfo::GetReferencedRowset](https://msdn.microsoft.com/en-us/library/ms721145.aspx) en *la referencia del*programador.  El parámetro *de iOrdinal* debe ser una columna de marcador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetInfoImpl \(Clase\)](../../data/oledb/irowsetinfoimpl-class.md)   
 [IRowsetInfoImpl::GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)   
 [IRowsetInfoImpl::GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)
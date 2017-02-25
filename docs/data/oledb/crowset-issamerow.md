---
title: "CRowset::IsSameRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset::IsSameRow"
  - "CRowset.IsSameRow"
  - "IsSameRow"
  - "ATL::CRowset::IsSameRow"
  - "ATL.CRowset.IsSameRow"
  - "CRowset<TAccessor>::IsSameRow"
  - "ATL.CRowset<TAccessor>.IsSameRow"
  - "CRowset<TAccessor>.IsSameRow"
  - "ATL::CRowset<TAccessor>::IsSameRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsSameRow (método)"
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CRowset::IsSameRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara la fila especificada con la fila actual.  
  
## Sintaxis  
  
```  
  
      HRESULT IsSameRow(   
   HROW hRow    
) const throw( );  
```  
  
#### Parámetros  
 `hRow`  
 \[in\] Un identificador de fila a comparar con la fila actual.  
  
## Valor devuelto  
 `HRESULT`estándar.  `S_OK` indica que las filas son iguales.  Para otros valores, vea [IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) en *la referencia del* programador de OLE [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)
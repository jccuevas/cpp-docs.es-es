---
title: "CRowset::AddRefRows | Microsoft Docs"
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
  - "CRowset<TAccessor>.AddRefRows"
  - "CRowset.AddRefRows"
  - "ATL.CRowset.AddRefRows"
  - "AddRefRows"
  - "CRowset::AddRefRows"
  - "CRowset<TAccessor>::AddRefRows"
  - "ATL::CRowset::AddRefRows"
  - "ATL.CRowset<TAccessor>.AddRefRows"
  - "ATL::CRowset<TAccessor>::AddRefRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRefRows (método)"
ms.assetid: 590b5a24-870f-4c42-b0c8-28491f368a82
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::AddRefRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las llamadas [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) para aumentar \(por uno\) el recuento de referencias asociadas al identificador de fila actual.  
  
## Sintaxis  
  
```  
  
HRESULT AddRefRows( ) throw( );  
  
```  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método incrementa el recuento de referencias para el identificador de fila actual.  Llamada [ReleaseRows](../../data/oledb/crowset-releaserows.md) para disminuir el recuento.  Las filas devueltas por los métodos move tienen un recuento de referencias de uno.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [CRowset::ReleaseRows](../../data/oledb/crowset-releaserows.md)
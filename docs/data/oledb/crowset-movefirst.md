---
title: "CRowset::MoveFirst | Microsoft Docs"
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
  - "CRowset<TAccessor>::MoveFirst"
  - "ATL::CRowset::MoveFirst"
  - "CRowset<TAccessor>.MoveFirst"
  - "CRowset::MoveFirst"
  - "CRowset.MoveFirst"
  - "ATL.CRowset.MoveFirst"
  - "ATL.CRowset<TAccessor>.MoveFirst"
  - "ATL::CRowset<TAccessor>::MoveFirst"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveFirst (método)"
ms.assetid: a17c0799-ead9-4d85-9a1d-8b17188d01e3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveFirst
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desplaza el cursor a la posición inicial y recupera la fila inicial.  
  
## Sintaxis  
  
```  
  
HRESULT MoveFirst( ) throw( );  
  
```  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Llama a [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) para colocar la ubicación de la NeXT\- búsqueda de nuevo a la posición inicial \(la posición que era la ubicación de la NeXT\- búsqueda cuando se creó el conjunto de filas\) y recupera la fila inicial.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)
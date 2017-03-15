---
title: "CRowset::MoveLast | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRowset<TAccessor>::MoveLast"
  - "CRowset<TAccessor>::MoveLast"
  - "ATL.CRowset.MoveLast"
  - "ATL::CRowset::MoveLast"
  - "CRowset<TAccessor>.MoveLast"
  - "MoveLast"
  - "CRowset::MoveLast"
  - "ATL.CRowset<TAccessor>.MoveLast"
  - "CRowset.MoveLast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveLast (método)"
ms.assetid: 81063578-ae9d-467b-8c88-81d8fc66e020
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::MoveLast
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desplaza el cursor a la última fila.  
  
## Sintaxis  
  
```  
  
HRESULT MoveLast( ) throw( );  
  
```  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Llama a [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) para colocar la ubicación de la NeXT\- búsqueda de nuevo a la posición pasada y recupera la última fila.  
  
 Este método requiere que se **DBPROP\_CANSCROLLBACKWARDS** establecido en `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas. \(Para mejorar el rendimiento, puede establecer **DBPROP\_QUICKRESTART** a `VARIANT_TRUE`.\)  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)
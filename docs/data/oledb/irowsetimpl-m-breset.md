---
title: "IRowsetImpl::m_bReset | Microsoft Docs"
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
  - "ATL.IRowsetImpl.m_bReset"
  - "IRowsetImpl.m_bReset"
  - "m_bReset"
  - "IRowsetImpl::m_bReset"
  - "ATL::IRowsetImpl::m_bReset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bReset"
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::m_bReset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un indicador de bit utilizado para determinar si la posición del cursor se define en el conjunto de filas.  
  
## Sintaxis  
  
```  
  
unsigned m_bReset:1;  
  
```  
  
## Comentarios  
 Si el consumidor llama a [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) con `lOffset` negativo o *los cuervos* y `m_bReset` es true, `GetNextRows` se mueve al final del conjunto de filas.  Si `m_bReset` es false, el consumidor recibe un código de error, de acuerdo con la especificación OLE DB.  El indicador de `m_bReset` obtiene el conjunto a **true** cuando se crea el conjunto de filas primero y cuando el consumidor llama a [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md).  Obtiene el conjunto a **false** cuando se llama a `GetNextRows`.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)
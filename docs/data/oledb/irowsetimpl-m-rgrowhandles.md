---
title: "IRowsetImpl::m_rgRowHandles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetImpl::m_rgRowHandles"
  - "IRowsetImpl.m_rgRowHandles"
  - "m_rgRowHandles"
  - "ATL::IRowsetImpl::m_rgRowHandles"
  - "ATL.IRowsetImpl.m_rgRowHandles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_rgRowHandles"
ms.assetid: d3c2578f-58c4-4301-bf59-cf101a523a95
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::m_rgRowHandles
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un mapa de los identificadores de fila contenido actualmente por el proveedor en respuesta a `GetNextRows`.  
  
## Sintaxis  
  
```  
  
MapClass  
 m_rgRowHandles;  
  
```  
  
## Comentarios  
 Los identificadores de fila se quitan llamando a `ReleaseRows`.  Vea [Información general de IRowsetImpl](../../data/oledb/irowsetimpl-class.md) para la definición *de MapClass*.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)
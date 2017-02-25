---
title: "IRowsetUpdateImpl::Update | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetUpdateImpl::Update"
  - "IRowsetUpdateImpl::Update"
  - "IRowsetUpdateImpl.Update"
  - "ATL.IRowsetUpdateImpl.Update"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Update (método)"
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetUpdateImpl::Update
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Transmite cualquier cambio realizado en la fila desde la búsqueda o la última actualización.  
  
## Sintaxis  
  
```  
  
      STDMETHOD ( Update )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus   
);  
```  
  
#### Parámetros  
 `hReserved`  
 \[in\] Corresponde a `hChapter` el parámetro en [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx).  
  
 Para otros parámetros, vea [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Los cambios se transmitidos llamando a [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md).  El consumidor debe llamar a [CRowset::Update](../../data/oledb/crowset-update.md) para que los cambios surtan efecto.  Establezca *el prgRowstatus* en un valor apropiado como se describe en [Estados de fila](https://msdn.microsoft.com/en-us/library/ms722752.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetUpdateImpl \(Clase\)](../../data/oledb/irowsetupdateimpl-class.md)
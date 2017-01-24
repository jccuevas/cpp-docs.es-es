---
title: "IOpenRowsetImpl::OpenRowset | Microsoft Docs"
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
  - "OpenRowset"
  - "IOpenRowsetImpl::OpenRowset"
  - "IOpenRowsetImpl.OpenRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenRowset (método)"
ms.assetid: 2ece8d6c-d165-4f1d-b155-8609bbb60eb6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOpenRowsetImpl::OpenRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abre y devuelve un conjunto de filas que incluya todas las filas de una sola tabla o índice.  
  
## Sintaxis  
  
```  
  
      HRESULT OpenRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset   
);  
```  
  
#### Parámetros  
 Vea [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Este método no se encuentra en ATLDB.H.  Es creado por el asistente para objetos ATL cuando se crea un proveedor.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IOpenRowsetImpl \(Clase\)](../../data/oledb/iopenrowsetimpl-class.md)
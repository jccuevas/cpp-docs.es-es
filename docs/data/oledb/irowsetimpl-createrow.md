---
title: "IRowsetImpl::CreateRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetImpl.CreateRow"
  - "ATL.IRowsetImpl.CreateRow"
  - "ATL::IRowsetImpl::CreateRow"
  - "CreateRow"
  - "IRowsetImpl::CreateRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRow (método)"
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::CreateRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un método auxiliar denominado por [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) para asignar nuevo **HROW**.  
  
## Sintaxis  
  
```  
  
      HRESULT CreateRow(  
   DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows   
);  
```  
  
#### Parámetros  
 *lRowsOffset*  
 Posición del cursor fila creado.  
  
 *cRowsObtained*  
 Una referencia que pasa de nuevo al usuario que indica el número de filas creadas.  
  
 *rgRows*  
 Una matriz de s de **HROW**devuelto al llamador con los identificadores de fila recién creados.  
  
## Comentarios  
 Si existe la fila, este método llama a [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y devolverá.  Si no, asigna una nueva instancia de la variable de la plantilla de RowClass y la agrega a [m\_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)
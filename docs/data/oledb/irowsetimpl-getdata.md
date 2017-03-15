---
title: "IRowsetImpl::GetData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetImpl.GetData"
  - "ATL::IRowsetImpl::GetData"
  - "IRowsetImpl::GetData"
  - "IRowsetImpl.GetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetData (método) [OLE DB]"
ms.assetid: cb15f1cc-bd25-4b74-93c3-db71aa93829c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::GetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera los datos desde la copia del conjunto de filas de la fila.  
  
## Sintaxis  
  
```  
  
      STDMETHOD( GetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData   
);  
```  
  
#### Parámetros  
 Vea [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) en *la referencia del*programador.  
  
 Algunos parámetros corresponden *a OLE DB parámetros de referencia* de nombres diferentes, que se describen en **IRowset::GetData**:  
  
|Parámetros de plantilla OLE DB|*Los parámetros de referencia del programador de OLE DB*|  
|------------------------------------|--------------------------------------------------------------|  
|*pDstData*|`pData`|  
  
## Comentarios  
 También controla la conversión de datos mediante la conversión de datos DLL de OLE DB.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)
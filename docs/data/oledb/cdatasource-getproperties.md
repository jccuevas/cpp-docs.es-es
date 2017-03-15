---
title: "CDataSource::GetProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource::GetProperties"
  - "ATL.CDataSource.GetProperties"
  - "CDataSource.GetProperties"
  - "ATL::CDataSource::GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties (método)"
ms.assetid: ffaecc17-9fe7-449e-94d6-43d31ad06cfc
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDataSource::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve información de la propiedad solicitada para el objeto de origen de datos conectado.  
  
## Sintaxis  
  
```  
  
      HRESULT GetProperties(   
   ULONG ulPropIDSets,   
   const DBPROPIDSET* pPropIDSet,   
   ULONG* pulPropertySets,   
   DBPROPSET** ppPropsets    
) const throw( );  
```  
  
#### Parámetros  
 Vea [IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx) en *la referencia del* programador de OLE [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Para obtener una única propiedad, utilice [GetProperty](../../data/oledb/cdatasource-getproperty.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)
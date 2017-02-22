---
title: "CRowset::GetRowStatus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset.GetRowStatus"
  - "ATL.CRowset<TAccessor>.GetRowStatus"
  - "ATL::CRowset<TAccessor>::GetRowStatus"
  - "CRowset::GetRowStatus"
  - "ATL::CRowset::GetRowStatus"
  - "CRowset<TAccessor>::GetRowStatus"
  - "ATL.CRowset.GetRowStatus"
  - "CRowset<TAccessor>.GetRowStatus"
  - "GetRowStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowStatus (método)"
ms.assetid: 7a29a235-cb7e-40c1-92ce-5441751febee
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::GetRowStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el estado de todas las filas.  
  
## Sintaxis  
  
```  
  
      HRESULT GetRowStatus(   
   DBPENDINGSTATUS* pStatus    
) const throw( );  
```  
  
#### Parámetros  
 `pStatus`  
 \[out\] Un puntero a una ubicación donde `GetRowStatus` devuelve el valor de estado.  Vea DBPENDINGSTATUS en la referencia del programador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método requiere la interfaz opcional `IRowsetUpdate`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)
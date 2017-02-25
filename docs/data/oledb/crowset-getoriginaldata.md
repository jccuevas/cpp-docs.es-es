---
title: "CRowset::GetOriginalData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset<TAccessor>.GetOriginalData"
  - "CRowset<TAccessor>::GetOriginalData"
  - "GetOriginalData"
  - "ATL::CRowset<TAccessor>::GetOriginalData"
  - "ATL.CRowset.GetOriginalData"
  - "CRowset::GetOriginalData"
  - "ATL::CRowset::GetOriginalData"
  - "CRowset.GetOriginalData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOriginalData (método)"
ms.assetid: 5b69d30e-34f4-41a4-a82d-cd175be88d53
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::GetOriginalData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llamadas **IRowsetUpdate::GetOriginalData** para recuperar los datos obtenidos de o transmitidos recientemente al origen de datos.  
  
## Sintaxis  
  
```  
  
HRESULT GetOriginalData( ) throw( );  
  
```  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método recupera los datos obtenidos de o transmitidos recientemente al origen de datos; no recupera los valores de cambios pendientes.  
  
 Este método requiere la interfaz opcional `IRowsetUpdate`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)
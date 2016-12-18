---
title: "CRowset::Update | Microsoft Docs"
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
  - "CRowset.Update"
  - "ATL.CRowset.Update"
  - "ATL.CRowset<TAccessor>.Update"
  - "ATL::CRowset<TAccessor>::Update"
  - "CRowset<TAccessor>::Update"
  - "CRowset::Update"
  - "CRowset<TAccessor>.Update"
  - "ATL::CRowset::Update"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Update (método)"
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Update
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Transmite los cambios pendientes realizados en la fila actual desde la última recuperación o llamada a de **Actualización** en ella.  
  
## Sintaxis  
  
```  
  
      HRESULT Update(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### Parámetros  
 `pcRows`  
 \[out\] Un puntero a la ubicación donde **Actualización** devuelve el número de filas que intentó actualizar, si es necesario.  
  
 `phRow`  
 \[out\] Un puntero a la ubicación donde **Actualización** devuelve el identificador de la fila que intentó actualizar.  No se devuelve ningún identificador si `phRow` es null.  
  
 `pStatus`  
 \[out\] Un puntero a la ubicación donde **Actualización** devuelve el valor de estado de fila.  No se devuelve ningún estado si `pStatus` es null.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Transmite los cambios pendientes realizados en la fila actual puesto que la fila se capturada o actualizada por última vez \(mediante **Actualización** o [UpdateAll](../../data/oledb/crowset-updateall.md)\).  Normalmente se llama a [SetData](../../data/oledb/crowset-setdata.md) para establecer valores de datos de columnas de una fila, y después llama **Actualización** para transmitir los cambios.  
  
 Este método requiere la interfaz opcional `IRowsetUpdate`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)
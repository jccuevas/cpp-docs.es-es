---
title: "CRowset::UpdateAll | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset::UpdateAll"
  - "ATL.CRowset.UpdateAll"
  - "CRowset<TAccessor>.UpdateAll"
  - "ATL.CRowset<TAccessor>.UpdateAll"
  - "UpdateAll"
  - "CRowset.UpdateAll"
  - "ATL::CRowset<TAccessor>::UpdateAll"
  - "CRowset<TAccessor>::UpdateAll"
  - "ATL::CRowset::UpdateAll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UpdateAll (método)"
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::UpdateAll
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Transmite los cambios pendientes realizados en todas las filas desde la última recuperación o llamada a de **Actualización** en ella.  
  
## Sintaxis  
  
```  
  
      HRESULT UpdateAll(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL    
) throw( );  
```  
  
#### Parámetros  
 `pcRows`  
 \[out\] Un puntero a la ubicación donde `UpdateAll` devuelve el número de filas que intentó actualizar, si es necesario.  
  
 `pphRow`  
 \[out\] Un puntero a la memoria de la que `UpdateAll` devuelve el identificador de la fila que intentó actualizar.  No se devuelve ningún identificador si `pphRow` es null.  
  
 `ppStatus`  
 \[out\] Un puntero a la ubicación donde **Actualización** devuelve el valor de estado de fila.  No se devuelve ningún estado si `ppStatus` es null.  
  
## Comentarios  
 Transmite los cambios pendientes realizados en todas las filas desde esas filas se capturadas o actualizadas por última vez mediante [Actualización](../../data/oledb/crowset-update.md) o `UpdateAll`.  `UpdateAll` actualizará cada fila se ha modificado, independientemente de si todavía tiene el identificador para ellos \(vea `pphRow`\) o no.  
  
 Por ejemplo, si utilizó **INSERT** para insertar cinco filas en un conjunto de filas, podría llamar a **Actualización** cinco veces o llamar a `UpdateAll` una vez para actualizarlas todas.  
  
 Este método requiere la interfaz opcional `IRowsetUpdate`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)
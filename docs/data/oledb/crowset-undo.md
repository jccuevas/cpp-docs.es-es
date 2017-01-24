---
title: "CRowset::Undo | Microsoft Docs"
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
  - "CRowset.Undo"
  - "ATL::CRowset<TAccessor>::Undo"
  - "CRowset<TAccessor>::Undo"
  - "ATL.CRowset.Undo"
  - "ATL.CRowset<TAccessor>.Undo"
  - "CRowset<TAccessor>.Undo"
  - "ATL::CRowset::Undo"
  - "CRowset::Undo"
  - "Undo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Undo (método)"
ms.assetid: 1ccd70e2-3931-41c4-893e-a05d0e295410
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Undo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Deshace los cambios realizados en una fila desde la última búsqueda o [Actualización](../../data/oledb/crowset-update.md).  
  
## Sintaxis  
  
```  
  
      HRESULT Undo(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### Parámetros  
 `pcRows`  
 \[out\] Un puntero a la ubicación donde **Deshacer** devuelve el número de filas que intentó deshacer si es necesario.  
  
 `phRow`  
 \[out\] Un puntero a la ubicación donde **Deshacer** devuelve una matriz de identificadores en todas las filas se intentó deshacer si es necesario.  
  
 `pStatus`  
 \[out\] Un puntero a la ubicación donde **Deshacer** devuelve el valor de estado de fila.  No se devuelve ningún estado si `pStatus` es null.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método requiere la interfaz opcional `IRowsetUpdate`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)
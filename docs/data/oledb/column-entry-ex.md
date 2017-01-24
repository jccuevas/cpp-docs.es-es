---
title: "COLUMN_ENTRY_EX | Microsoft Docs"
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
  - "COLUMN_ENTRY_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_EX (macro)"
ms.assetid: dfad1b67-51c3-4289-b89a-da42d7e8bb88
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.  
  
## Sintaxis  
  
```  
  
COLUMN_ENTRY_EX(  
nOrdinal  
,   
wType  
,   
nLength  
,   
nPrecision  
,   
nScale  
,   
data  
,   
length  
,   
status  
 )  
  
```  
  
#### Parámetros  
 Vea [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en *la referencia del*programador.  
  
 `nOrdinal`  
 \[in\] El número de columnas.  
  
 `wType`  
 \[in\] El tipo de datos.  
  
 `nLength`  
 \[in\] El tamaño de datos en bytes.  
  
 `nPrecision`  
 \[in\] La precisión máxima para utilizar cuando obtiene datos y `wType` es `DBTYPE_NUMERIC`.  De lo contrario, este parámetro se omite.  
  
 `nScale`  
 \[in\] Escala para utilizar cuando obtiene datos y `wType` es `DBTYPE_NUMERIC` o **DBTYPE\_DECIMAL**.  
  
 `data`  
 \[in\] El miembro de datos correspondiente en el registro de usuario.  
  
 *length*  
 \[in\] La variable que se enlazará a la longitud de la columna.  
  
 *status*  
 \[in\] La variable que se enlazará el estado de la columna.  
  
## Comentarios  
 La macro de `COLUMN_ENTRY_EX` se utiliza en los lugares siguientes:  
  
-   Entre [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md) y macros de [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) .  
  
-   Entre [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) y macros de [END\_ACCESSOR](../../data/oledb/end-accessor.md) .  
  
-   Entre [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md) y macros de [END\_PARAM\_MAP](../../data/oledb/end-param-map.md) .  
  
## Ejemplo  
 Vea [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)
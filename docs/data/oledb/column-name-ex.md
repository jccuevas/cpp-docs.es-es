---
title: "COLUMN_NAME_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_NAME_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_NAME_EX (macro)"
ms.assetid: 4f916a85-f6ae-464a-9cbe-0a56dbb274a6
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_NAME_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un enlace en el conjunto de filas a la columna concreta en el conjunto de filas.  Similar a [COLUMN\_NAME](../../data/oledb/column-name.md), salvo que esta macro también toma el tipo de datos, tamaño, precisión, escala, longitud de la columna, y el estado de la columna.  
  
## Sintaxis  
  
```  
  
COLUMN_NAME_EX(  
pszName  
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
status )  
```  
  
#### Parámetros  
 `pszName`  
 \[in\] Un puntero al nombre de columna.  El nombre debe ser una cadena Unicode.  Esto se puede lograr poniendo una “l” delante del nombre, por ejemplo: `L"MyColumn"`.  
  
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
 Vea [COLUMN\_NAME](../../data/oledb/column-name.md) para información donde se utilizan macros de **COLUMN\_NAME\_\*** .  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_NAME](../../data/oledb/column-name.md)   
 [COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)
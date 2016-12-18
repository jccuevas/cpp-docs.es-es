---
title: "COLUMN_NAME | Microsoft Docs"
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
  - "COLUMN_NAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_NAME (macro)"
ms.assetid: a213b9a0-2148-4a08-9111-d9fa8fdec462
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_NAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un enlace en el conjunto de filas a la columna concreta en el conjunto de filas.  Similar a [COLUMN\_ENTRY](../../data/oledb/column-entry.md), salvo que esta macro toma el nombre de columna en lugar del número de columnas.  
  
## Sintaxis  
  
```  
  
COLUMN_NAME(  
pszName  
,   
data  
 )  
  
```  
  
#### Parámetros  
 `pszName`  
 \[in\] Un puntero al nombre de columna.  El nombre debe ser una cadena Unicode.  Esto se puede lograr poniendo una “l” delante del nombre, por ejemplo: `L"MyColumn"`.  
  
 `data`  
 \[in\] El miembro de datos correspondiente en el registro de usuario.  
  
## Comentarios  
 Las macros de **COLUMN\_NAME\_\*** se utilizan en los mismos lugares como [COLUMN\_ENTRY](../../data/oledb/column-entry.md):  
  
-   Entre [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md) y macros de [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) .  
  
-   Entre [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) y macros de [END\_ACCESSOR](../../data/oledb/end-accessor.md) .  
  
-   Entre [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md) y macros de [END\_PARAM\_MAP](../../data/oledb/end-param-map.md) .  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)   
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
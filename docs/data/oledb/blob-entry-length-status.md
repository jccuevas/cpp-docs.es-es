---
title: "BLOB_ENTRY_LENGTH_STATUS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLOB_ENTRY_LENGTH_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_ENTRY_LENGTH_STATUS (macro)"
ms.assetid: 09da67de-421b-4853-9a26-760e38324502
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# BLOB_ENTRY_LENGTH_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza con `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP` para enlazar un objeto binario grande \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\).  Similar a [BLOB\_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro también obtiene la longitud y el estado de la columna del BLOB.  
  
## Sintaxis  
  
```  
  
BLOB_ENTRY_LENGTH_STATUS(  
nOrdinal  
,   
IID  
,   
flags  
,   
data  
, length, status )  
```  
  
#### Parámetros  
 `nOrdinal`  
 \[in\] El número de columnas.  
  
 *IID*  
 \[in\] Interfaz GUID, como **IDD\_ISequentialStream**, utilizado para recuperar BLOB.  
  
 `flags`  
 \[in\] marcas de Almacenamiento\- modo definida por el modelo de almacenamiento estructurado OLE \(por ejemplo, **STGM\_READ**\).  
  
 `data`  
 \[in\] El miembro de datos correspondiente en el registro de usuario.  
  
 *length*  
 \[out\] La longitud \(real\) en bytes de la columna del BLOB.  
  
 *status*  
 \[out\] El estado de la columna de datos BLOB.  
  
## Ejemplo  
 Vea [¿Cómo Poder recupero BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB\_ENTRY\_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB\_ENTRY\_STATUS](../../data/oledb/blob-entry-status.md)
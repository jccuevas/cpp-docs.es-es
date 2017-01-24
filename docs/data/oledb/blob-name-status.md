---
title: "BLOB_NAME_STATUS | Microsoft Docs"
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
  - "BLOB_NAME_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_NAME_STATUS (macro)"
ms.assetid: 4564e4a0-8e5e-436a-bd1e-012d2a1b8642
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BLOB_NAME_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza con `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP` para enlazar un objeto binario grande \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\).  Similar a [BLOB\_NAME](../../data/oledb/blob-name.md), salvo que esta macro también obtiene el estado de la columna de datos BLOB.  
  
## Sintaxis  
  
```  
  
BLOB_NAME_STATUS(  
pszName  
,   
IID  
,   
flags  
,   
data  
, status )  
```  
  
#### Parámetros  
 `pszName`  
 \[in\] Un puntero al nombre de columna.  El nombre debe ser una cadena Unicode.  Esto se puede lograr poniendo una “l” delante del nombre, por ejemplo: `L"MyColumn"`.  
  
 *IID*  
 \[in\] Interfaz GUID, como **IDD\_ISequentialStream**, utilizado para recuperar BLOB.  
  
 `flags`  
 \[in\] marcas de Almacenamiento\- modo definida por el modelo de almacenamiento estructurado OLE \(por ejemplo, **STGM\_READ**\).  
  
 `data`  
 \[in\] El miembro de datos correspondiente en el registro de usuario.  
  
 *status*  
 \[out\] El estado del campo del BLOB.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_NAME](../../data/oledb/blob-name.md)   
 [BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)
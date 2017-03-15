---
title: "BLOB_NAME | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLOB_NAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_NAME (macro)"
ms.assetid: 757acd0d-946d-447d-937e-94ecd700ba38
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# BLOB_NAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza con `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP` para enlazar un objeto binario grande \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\).  Similar a [BLOB\_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro toma un nombre de columna en lugar de un número de columnas.  
  
## Sintaxis  
  
```  
  
BLOB_NAME(  
pszName  
,   
IID  
,   
flags  
,   
data )  
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
  
## Ejemplo  
 Vea [¿Cómo Poder recupero BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB\_NAME\_STATUS](../../data/oledb/blob-name-status.md)
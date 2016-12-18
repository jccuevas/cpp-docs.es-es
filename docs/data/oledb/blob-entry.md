---
title: "BLOB_ENTRY | Microsoft Docs"
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
  - "BLOB_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_ENTRY (macro)"
ms.assetid: 89e40678-0869-49ed-b502-0fa2630a9081
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BLOB_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza con `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP` para enlazar un objeto binario grande \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\).  
  
## Sintaxis  
  
```  
  
BLOB_ENTRY(  
nOrdinal  
,  
 IID  
,   
flags  
,   
data  
 )  
  
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
  
## Ejemplo  
 Vea [¿Cómo Poder recupero BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_ENTRY\_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB\_ENTRY\_LENGTH\_STATUS](../../data/oledb/blob-entry-length-status.md)   
 [BLOB\_ENTRY\_STATUS](../../data/oledb/blob-entry-status.md)
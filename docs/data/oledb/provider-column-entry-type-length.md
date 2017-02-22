---
title: "PROVIDER_COLUMN_ENTRY_TYPE_LENGTH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_COLUMN_ENTRY_TYPE_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_TYPE_LENGTH (macro)"
ms.assetid: a60b1a8b-0903-4ff4-91ec-ed62126449fb
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una columna concreta admitida por el proveedor.  
  
## Sintaxis  
  
```  
  
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(  
name  
, ordinal, dbtype, size, member )  
```  
  
#### Parámetros  
 *nombre*  
  
 \[in\] El nombre de columna.  
  
 `ordinal`  
 \[in\] El número de columnas.  A menos que la columna es una columna de marcador, el número de columnas no debe ser 0.  
  
 `dbtype`  
 \[in\] El tipo de datos en [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
 `size`  
 \[in\] El tamaño de la columna en bytes.  
  
 `member`  
 \[in\] La variable miembro de la clase de datos que almacena los datos.  
  
## Comentarios  
 Similar a [PROVIDER\_COLUMN\_ENTRY\_LENGTH](../../data/oledb/provider-column-entry-length.md) pero también permite especificar el tipo de datos así como el tamaño de la columna.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
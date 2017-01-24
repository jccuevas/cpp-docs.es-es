---
title: "PROVIDER_COLUMN_ENTRY_STR | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_STR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_STR (macro)"
ms.assetid: f1c27dd6-9ab8-4821-8685-d4dd15e76e88
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_STR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una columna concreta admitida por el proveedor.  
  
## Sintaxis  
  
```  
  
PROVIDER_COLUMN_ENTRY_STR(  
name  
, ordinal, member )  
```  
  
#### Parámetros  
 *name*  
 \[in\] El nombre de columna.  
  
 `ordinal`  
 \[in\] El número de columnas.  A menos que la columna es una columna de marcador, el número de columnas no debe ser 0.  
  
 `member`  
 \[in\] La variable miembro de la clase de datos que almacena los datos.  
  
## Comentarios  
 Use esta macro cuando los datos de columna se supone que [DBTYPE\_STR](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
## Ejemplo  
 Vea [BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
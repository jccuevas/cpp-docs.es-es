---
title: "BEGIN_SCHEMA_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_SCHEMA_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_SCHEMA_MAP (macro)"
ms.assetid: 4e751023-35bc-4efd-9018-5448dd1ad751
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BEGIN_SCHEMA_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica el principio de un mapa de esquema.  
  
## Sintaxis  
  
```  
  
      BEGIN_SCHEMA_MAP(  
   SchemaClass   
);  
```  
  
#### Parámetros  
 *SchemaClass*  
 La clase que contiene el MAPA.  Esto normalmente será la clase de sesión.  
  
## Comentarios  
 Vea [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre los conjuntos de filas de esquema.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [SCHEMA\_ENTRY](../../data/oledb/schema-entry.md)   
 [END\_SCHEMA\_MAP](../../data/oledb/end-schema-map.md)   
 [IDBSchemaRowsetImpl \(Clase\)](../../data/oledb/idbschemarowsetimpl-class.md)
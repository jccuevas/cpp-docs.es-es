---
title: "SCHEMA_ENTRY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SCHEMA_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SCHEMA_ENTRY (macro)"
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# SCHEMA_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asocia un GUID a una clase.  
  
## Sintaxis  
  
```  
  
      SCHEMA_ENTRY(  
   guid,  
   rowsetClass   
);   
```  
  
#### Parámetros  
 `guid`  
 Un conjunto de filas de esquema GUID.  Vea [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en *la referencia del* programador para obtener una lista de conjuntos de filas de esquema y su GUID.  
  
 *rowsetClass*  
 La clase que se creará para representar el conjunto de filas de esquema.  
  
## Comentarios  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) puede ver el mapa para obtener una lista de GUID, o puede crear un conjunto de filas si se da un GUID.  El conjunto de filas de esquema que `IDBSchemaRowsetImpl` crea es similar a `CRowsetImpl`estándar \- clase derivada, a menos que proporcione un método de **Ejecución** que tiene la siguiente firma:  
  
 `HRESULT Execute (LONG* pcRowsAffected, ULONG cRestrictions,`  
  
 `const VARIANT* rgRestrictions)`  
  
 Esta función de **Ejecución** rellena los datos del conjunto de filas.  El asistente para proyectos ATL crea, como se describe en [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en *la referencia del*programador, tres conjuntos de filas de esquema iniciales del proyecto para cada uno de los tres esquemas obligatorios OLE DB:  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA\_COLUMNS**  
  
-   **DBSCHEMA\_PROVIDER\_TYPES**  
  
 El asistente también agrega tres entradas correspondientes en el mapa de esquema.  Vea [Crear un proveedor de plantillas OLE DB](../../data/oledb/creating-an-ole-db-provider.md) para obtener más información sobre cómo utilizar el asistente para crear un proveedor.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN\_SCHEMA\_MAP](../../data/oledb/begin-schema-map.md)   
 [END\_SCHEMA\_MAP](../../data/oledb/end-schema-map.md)
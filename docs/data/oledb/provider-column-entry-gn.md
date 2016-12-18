---
title: "PROVIDER_COLUMN_ENTRY_GN | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_GN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_GN (macro)"
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_GN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una columna concreta admitida por el proveedor.  
  
## Sintaxis  
  
```  
  
PROVIDER_COLUMN_ENTRY_GN (  
name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### Parámetros  
 *name*  
 \[in\] El nombre de columna.  
  
 `ordinal`  
 \[in\] El número de columnas.  A menos que la columna es una columna de marcador, el número de columnas no debe ser 0.  
  
 `flags`  
 \[in\] Especifica cómo se devuelven los datos.  Vea la descripción de `dwFlags` en [Estructuras de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *colSize*  
 \[in\] El tamaño de columna.  
  
 `dbtype`  
 \[in\] Indica el tipo de datos del valor.  Vea la descripción de **wType** en [Estructuras de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *precision*  
 \[in\] Indica la precisión para utilizar cuando obtiene datos si el *dbType* es `DBTYPE_NUMERIC` o **DBTYPE\_DECIMAL**.  Vea la descripción de **bPrecision** en [Estructuras de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `scale`  
 \[in\] Indica la escala para utilizar cuando obtiene datos si el dbType es `DBTYPE_NUMERIC` o **DBTYPE\_DECIMAL**.  Vea la descripción de **bScale** en [Estructuras de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `guid`  
 Un conjunto de filas de esquema GUID.  Vea [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en *la referencia del* programador para obtener una lista de conjuntos de filas de esquema y su GUID.  
  
## Comentarios  
 Permite especificar el tamaño, el tipo de datos, la precisión, escala, y el conjunto de filas de esquema GUID de la columna.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
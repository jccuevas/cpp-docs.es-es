---
title: "PROVIDER_COLUMN_ENTRY_LENGTH | Microsoft Docs"
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
  - "PROVIDER_COLUMN_ENTRY_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_LENGTH (macro)"
ms.assetid: b4a67246-c049-4622-bb65-242cc8cae4be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROVIDER_COLUMN_ENTRY_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una columna concreta admitida por el proveedor.  
  
## Sintaxis  
  
```  
  
PROVIDER_COLUMN_ENTRY_LENGTH(  
name  
, ordinal, size, member )  
```  
  
#### Parámetros  
 *name*  
 \[in\] El nombre de columna.  
  
 `ordinal`  
 \[in\] El número de columnas.  A menos que la columna es una columna de marcador, el número de columnas no debe ser 0.  
  
 `size`  
 \[in\] El tamaño de la columna en bytes.  
  
 `member`  
 \[in\] La variable miembro en `dataClass` que almacena los datos de columna.  
  
## Comentarios  
 Permite especificar el tamaño de columna.  
  
## Ejemplo  
 Vea [BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
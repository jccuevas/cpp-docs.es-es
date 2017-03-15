---
title: "PROVIDER_COLUMN_ENTRY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_COLUMN_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY (macro)"
ms.assetid: 7921cfc1-aa9c-493e-8fc4-9d4294cafe72
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# PROVIDER_COLUMN_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una columna concreta admitida por el proveedor.  
  
## Sintaxis  
  
```  
  
PROVIDER_COLUMN_ENTRY (  
name  
, ordinal, member )  
```  
  
#### Parámetros  
 *name*  
 \[in\] El nombre de columna.  
  
 `ordinal`  
 \[in\] El número de columnas.  A menos que la columna es una columna de marcador, el número de columnas no debe ser 0.  
  
 `member`  
 \[in\] La variable miembro en `dataClass` correspondiente a la columna.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
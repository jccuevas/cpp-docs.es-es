---
title: "BEGIN_ACCESSOR_MAP | Microsoft Docs"
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
  - "BEGIN_ACCESSOR_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_ACCESSOR_MAP (macro)"
ms.assetid: e6d6e3a4-62fa-4e49-8c53-caf8c9d20091
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BEGIN_ACCESSOR_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marca el principio de las entradas de asignación de descriptores de acceso.  
  
## Sintaxis  
  
```  
  
BEGIN_ACCESSOR_MAP(  
x  
,   
num  
 )  
  
```  
  
#### Parámetros  
 *x*  
 \[in\] Nombre de la clase de registro de usuario.  
  
 *num*  
 \[in\] Número de descriptores de acceso de esta asignación de descriptores de acceso.  
  
## Comentarios  
 Si hay varios descriptores de acceso en un conjunto de filas, debe especificar `BEGIN_ACCESSOR_MAP` al principio y usar la macro `BEGIN_ACCESSOR` para cada descriptor de acceso individual. La macro `BEGIN_ACCESSOR` se completa con la macro `END_ACCESSOR`. La asignación de descriptores de acceso se completa con la macro `END_ACCESSOR_MAP`.  
  
 Si solo tiene un descriptor de acceso en el registro de usuario, use la macro [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md).  
  
## Ejemplo  
 [!CODE [NVC_OLEDB_Consumer#15](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#15)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)
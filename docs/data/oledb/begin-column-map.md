---
title: "BEGIN_COLUMN_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_COLUMN_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_COLUMN_MAP (macro)"
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# BEGIN_COLUMN_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marca el inicio de una entrada de mapa de columnas.  
  
## Sintaxis  
  
```  
  
BEGIN_COLUMN_MAP(  
x  
 )  
  
```  
  
#### Parámetros  
 *x*  
 \[in\] Nombre de la clase de registro de usuario derivada de `CAccessor`.  
  
## Comentarios  
 Esta macro se usa en el caso de un único descriptor de acceso en un conjunto de filas. Si tiene varios descriptores de acceso en un conjunto de filas, use [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md).  
  
 La macro `BEGIN_COLUMN_MAP` se completa con la macro `END_COLUMN_MAP`. Esta macro se usa cuando solamente hay un descriptor de acceso necesario en el registro de usuario.  
  
 Las columnas corresponden a los campos del conjunto de filas que quiere enlazar.  
  
## Ejemplo  
 Este es un mapa de columnas y parámetros de ejemplo:  
  
 [!CODE [NVC_OLEDB_Consumer#16](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#16)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)
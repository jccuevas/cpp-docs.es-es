---
title: "COLUMN_ENTRY_TYPE_SIZE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_TYPE_SIZE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_TYPE_SIZE (macro)"
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_ENTRY_TYPE_SIZE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un enlace a la columna concreta de la base de datos.  Admite `type` y los parámetros de `size` .  
  
## Sintaxis  
  
```  
  
COLUMN_ENTRY_TYPE_SIZE(  
nOrdinal  
,   
wType  
,   
nLength  
,   
data  
 )  
  
```  
  
#### Parámetros  
 `nOrdinal`  
 \[in\] El número de columnas.  
  
 `wType`  
 \[in\] Tipo de datos de entrada de la columna.  
  
 `nLength`  
 \[in\] Tamaño de la entrada de la columna en bytes.  
  
 `data`  
 \[in\] El miembro de datos correspondiente en el registro de usuario.  
  
## Comentarios  
 Esta macro es una variante especializada de la macro de [COLUMN\_ENTRY](../../data/oledb/column-entry.md) que proporciona un medio para especificar el tamaño de datos y el tipo.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)
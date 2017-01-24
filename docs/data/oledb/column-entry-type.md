---
title: "COLUMN_ENTRY_TYPE | Microsoft Docs"
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
  - "COLUMN_ENTRY_TYPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_TYPE (macro)"
ms.assetid: ac424261-ff6c-443b-a197-2cec8d78d738
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY_TYPE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un enlace a la columna concreta de la base de datos.  Admite el parámetro de `type` .  
  
## Sintaxis  
  
```  
  
COLUMN_ENTRY_TYPE (  
nOrdinal  
,   
wType  
,   
data  
 )  
  
```  
  
#### Parámetros  
 `nOrdinal`  
 \[in\] El número de columnas.  
  
 `wType`  
 \[in\] Tipo de datos de entrada de la columna.  
  
 `data`  
 \[in\] El miembro de datos correspondiente en el registro de usuario.  
  
## Comentarios  
 Esta macro es una variante especializada de la macro de [COLUMN\_ENTRY](../../data/oledb/column-entry.md) que proporciona un medio para especificar el tipo de datos.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)
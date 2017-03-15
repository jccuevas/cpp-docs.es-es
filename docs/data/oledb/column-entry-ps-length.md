---
title: "COLUMN_ENTRY_PS_LENGTH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_PS_LENGTH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_PS_LENGTH (macro)"
ms.assetid: d63ab895-a4df-4183-ac09-cf2311222408
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_ENTRY_PS_LENGTH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.  
  
## Sintaxis  
  
```  
  
COLUMN_ENTRY_PS_LENGTH(  
nOrdinal  
,   
nPrecision  
,   
nScale  
,   
data  
,   
length  
 )  
  
```  
  
#### Parámetros  
 Vea [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en *la referencia del*programador.  
  
 `nOrdinal`  
 \[in\] El número de columnas, empezando por uno.  El marcador corresponde a la columna cero.  
  
 `nPrecision`  
 \[in\] Precisión máxima de la columna que desea enlazar.  
  
 `nScale`  
 \[in\] La escala de la columna que desea enlazar.  
  
 `data`  
 \[in\] El miembro de datos correspondiente en el registro de usuario.  
  
 *length*  
 \[in\] La variable que se enlazará a la longitud de la columna.  
  
## Comentarios  
 Permite especificar la precisión y la escala de la columna que desea enlazar.  Esta macro admite la variable length.  Se utiliza en los lugares siguientes:  
  
-   Entre [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md) y macros de [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) .  
  
-   Entre [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) y macros de [END\_ACCESSOR](../../data/oledb/end-accessor.md) .  
  
-   Entre [BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md) y macros de [END\_PARAM\_MAP](../../data/oledb/end-param-map.md) .  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)
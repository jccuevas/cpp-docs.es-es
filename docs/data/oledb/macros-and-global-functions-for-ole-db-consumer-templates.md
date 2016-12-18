---
title: "Macros y funciones globales para las plantillas de consumidor OLE DB | Microsoft Docs"
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
  - "vc.templates.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros, plantilla de consumidor OLE DB"
  - "plantillas de consumidor OLE DB, macros"
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Macros y funciones globales para las plantillas de consumidor OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las plantillas de consumidor OLE DB incluye las siguientes macros y funciones globales:  
  
### Funciones globales  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|Vuelca información de registro de errores de OLE DB al dispositivo de volcado si se devuelve un error.|  
  
### Macros de mapa de descriptor de acceso  
  
|||  
|-|-|  
|[BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)|Marca el principio de una entrada de descriptor de acceso.|  
|[BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)|Marca el principio de las entradas del mapa del descriptor.|  
|[END\_ACCESSOR](../../data/oledb/end-accessor.md)|Marca el final de una entrada de descriptor de acceso.|  
|[END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)|Marca el final de las entradas del mapa del descriptor.|  
  
### Macros de mapa de columnas  
  
|||  
|-|-|  
|[BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)|Marca el principio de las entradas del mapa de columnas en la clase de registro de usuario.|  
|[BLOB\_ENTRY](../../data/oledb/blob-entry.md)|Se utiliza para enlazar un objeto binario grande \(BLOB\).|  
|[BLOB\_ENTRY\_LENGTH](../../data/oledb/blob-entry-length.md)|Informa de la longitud de la columna de datos BLOB.|  
|[BLOB\_ENTRY\_LENGTH\_STATUS](../../data/oledb/blob-entry-length-status.md)|Informes la longitud y el estado de la columna de datos BLOB.|  
|[BLOB\_ENTRY\_STATUS](../../data/oledb/blob-entry-status.md)|Obtiene el estado de la columna de datos BLOB.|  
|[BLOB\_NAME](../../data/oledb/blob-name.md)|Se utiliza para enlazar un nombre de objeto binario grande por columna.|  
|[BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)|Informa de la longitud de la columna de datos BLOB.|  
|[BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)|Informes la longitud y el estado de la columna de datos BLOB.|  
|[BLOB\_NAME\_STATUS](../../data/oledb/blob-name-status.md)|Obtiene el estado de la columna de datos BLOB.|  
|[BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)|Representa una entrada de marcador en el conjunto de filas.  Una entrada de marcador es una clase especial de entrada de la columna.|  
|[COLUMN\_ENTRY](../../data/oledb/column-entry.md)|Representa un enlace a una columna concreta de la base de datos.|  
|[COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)|Representa un enlace a la columna concreta de la base de datos.  Admite `type`, *longitud*, *precisión*, `scale`, y parámetros *de estado* .|  
|[COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)|Representa un enlace a la columna concreta de la base de datos.  Admite la variable length.|  
|[COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)|Representa un enlace a la columna concreta de la base de datos.  Admite parámetros *estado* y *longitud*.|  
|[COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)|Representa un enlace a la columna concreta de la base de datos.  Admite la *precisión* y los parámetros de `scale` .|  
|[COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)|Representa un enlace a la columna concreta de la base de datos.  Admite la variable *de longitud* , *precisión* y los parámetros de `scale` .|  
|[COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)|Representa un enlace a la columna concreta de la base de datos.  Admite variables *estado* y *longitud*, *precisión* y `scale` .|  
|[COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)|Representa un enlace a la columna concreta de la base de datos.  Admite la variable *de estado* , *la precisión* y los parámetros de `scale` .|  
|[COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)|Representa un enlace a la columna concreta de la base de datos.  Admite la variable *de estado* .|  
|[COLUMN\_ENTRY\_TYPE](../../data/oledb/column-entry-type.md)|Representa un enlace a una columna concreta de la base de datos.  Admite el parámetro de `type` .|  
|[COLUMN\_ENTRY\_TYPE\_SIZE](../../data/oledb/column-entry-type-size.md)|Representa un enlace a la columna concreta de la base de datos.  Admite `type` y los parámetros de `size` .|  
|[COLUMN\_NAME](../../data/oledb/column-name.md)|Representa un enlace a una columna concreta de la base de datos por nombre.|  
|[COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de tipo de datos, el tamaño, la precisión, la escala, la longitud de la columna, y el estado de la columna.|  
|[COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de la longitud de la columna.|  
|[COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de longitud y estado de la columna.|  
|[COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de la precisión y la escala.|  
|[COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de la precisión, la escala, y la longitud de la columna.|  
|[COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de la precisión, la escala, la longitud de la columna, y el estado de la columna.|  
|[COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de la precisión, la escala, y el estado de la columna.|  
|[COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación del estado de la columna.|  
|[COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de tipo de datos.|  
|[COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de tipo de datos, la precisión, y de la escala.|  
|[COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación de tipo de datos y el tamaño.|  
|[COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre.  Admite la especificación del estado del tipo de datos y columna.|  
|[END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)|Marca el final de las entradas del mapa de columnas.|  
  
### Macros de comando  
  
|||  
|-|-|  
|[DEFINE\_COMMAND](../../data/oledb/define-command.md)|Especifica el comando que se utilizó para crear el conjunto de filas al utilizar la clase de [CCommand](../../data/oledb/ccommand-class.md) .  Acepta solo los tipos de cadenas que coinciden con el tipo de aplicación especificado \(ANSI o Unicode\).  Se recomienda utilizar [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) en lugar de `DEFINE_COMMAND`.|  
|[DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md)|Especifica el comando que se utilizó para crear el conjunto de filas al utilizar la clase de [CCommand](../../data/oledb/ccommand-class.md) .  Admite ANSI y aplicaciones de Unicode.|  
  
### Macros de mapa de parámetros  
  
|||  
|-|-|  
|[BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md)|Marca el principio de las entradas del mapa de parámetros en la clase de registro de usuario.|  
|[END\_PARAM\_MAP](../../data/oledb/end-param-map.md)|Marca el final de las entradas del mapa de parámetros.|  
|[SET\_PARAM\_TYPE](../../data/oledb/set-param-type.md)|Especifica las macros de `COLUMN_ENTRY` que siguen la macro de `SET_PARAM_TYPE` como entrada, salida, o entrada\/salida.|  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
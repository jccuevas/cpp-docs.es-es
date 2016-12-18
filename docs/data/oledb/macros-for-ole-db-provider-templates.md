---
title: "Macros para plantillas de proveedores OLE DB | Microsoft Docs"
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
  - "macros, Plantillas de proveedores OLE DB"
  - "macros para plantillas de proveedores OLE DB"
  - "plantillas del proveedor OLE DB, macros"
  - "macros para plantillas de proveedores (OLE DB)"
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Macros para plantillas de proveedores OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las macros de proveedor de plantillas OLE DB proporcionan funcionalidad en las categorías siguientes:  
  
### Macros de mapa del conjunto de propiedades  
  
|||  
|-|-|  
|[BEGIN\_PROPERTY\_SET](../../data/oledb/begin-property-set.md)|Marca el principio de un conjunto de propiedades.|  
|[BEGIN\_PROPERTY\_SET\_EX](../../data/oledb/begin-property-set-ex.md)|Marca el principio de un conjunto de propiedades.|  
|[BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)|Marca el principio de una propiedad establecida que se puede ocultar o definir fuera del ámbito del proveedor.|  
|[CHAIN\_PROPERTY\_SET](../../data/oledb/chain-property-set.md)|Grupos de propiedades de cadenas juntas.|  
|[END\_PROPERTY\_SET](../../data/oledb/end-property-set.md)|Marca el final de un conjunto de propiedades.|  
|[END\_PROPSET\_MAP](../../data/oledb/end-propset-map.md)|Marca el final de un mapa del conjunto de propiedades.|  
|[PROPERTY\_INFORMATION\_ENTRY](../../data/oledb/property-info-entry.md)|Establece una propiedad específica en una propiedad establecida en un valor predeterminado.|  
|[PROPERTY\_INFORMATION\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por el usuario.  También permite establecer marcadores y opciones.|  
|[PROPERTY\_INFORMATION\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por el usuario.|  
  
### Macros de mapa de columnas  
  
|||  
|-|-|  
|[BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md)|Marca el principio de las entradas del mapa de columnas del proveedor.|  
|[END\_PROVIDER\_COLUMN\_MAP](../../data/oledb/end-provider-column-map.md)|Marca el final de las entradas del mapa de columnas del proveedor.|  
|[PROVIDER\_COLUMN\_ENTRY](../../data/oledb/provider-column-entry.md)|Representa una columna concreta admitida por el proveedor.|  
|[PROVIDER\_COLUMN\_ENTRY\_GN](../../data/oledb/provider-column-entry-gn.md)|Representa una columna concreta admitida por el proveedor.  Puede especificar el tamaño, el tipo de datos, la precisión, escala, y el conjunto de filas de esquema GUID de la columna.|  
|[PROVIDER\_COLUMN\_ENTRY\_FIXED](../../data/oledb/provider-column-entry-fixed.md)|Representa una columna concreta admitida por el proveedor.  Puede especificar el tipo de datos de columna.|  
|[PROVIDER\_COLUMN\_ENTRY\_LENGTH](../../data/oledb/provider-column-entry-length.md)|Representa una columna concreta admitida por el proveedor.  Puede especificar el tamaño de columna.|  
|[PROVIDER\_COLUMN\_ENTRY\_STR](../../data/oledb/provider-column-entry-str.md)|Representa una columna concreta admitida por el proveedor.  Supone que el tipo de columna es una cadena.|  
|[PROVIDER\_COLUMN\_ENTRY\_TYPE\_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|Representa una columna concreta admitida por el proveedor.  Como PROVIDER\_COLUMN\_ENTRY\_LENGTH, pero también permite especificar el tipo de datos así como el tamaño de la columna.|  
|[PROVIDER\_COLUMN\_ENTRY\_WSTR](../../data/oledb/provider-column-entry-wstr.md)|Representa una columna concreta admitida por el proveedor.  Supone que el tipo de columna es una cadena de caracteres Unicode.|  
  
### Macros de conjunto de filas de esquema  
  
|||  
|-|-|  
|[BEGIN\_SCHEMA\_MAP](../../data/oledb/begin-schema-map.md)|Marca el principio de un mapa de esquema.|  
|[SCHEMA\_ENTRY](../../data/oledb/schema-entry.md)|Asocia un GUID a una clase.|  
|[END\_SCHEMA\_MAP](../../data/oledb/end-schema-map.md)|Marca el final de un mapa de esquema.|  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [Referencia de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)
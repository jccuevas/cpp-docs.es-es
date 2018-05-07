---
title: Macros para plantillas de proveedores OLE DB | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab7611c49f625a36023b4e31bf6aff47ab16f156
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="macros-for-ole-db-provider-templates"></a>Macros para plantillas de proveedores OLE DB
Las macros de plantillas del proveedor OLE DB proporcionan funcionalidad en las siguientes categorías:  
  
### <a name="property-set-map-macros"></a>Macros de mapa de conjunto de propiedades  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](../../data/oledb/begin-property-set.md)|Marca el principio de un conjunto de propiedades.|  
|[BEGIN_PROPERTY_SET_EX](../../data/oledb/begin-property-set-ex.md)|Marca el principio de un conjunto de propiedades.|  
|[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)|El principio de una propiedad que establece las marcas se pueden ocultas o definidas fuera del ámbito del proveedor.|  
|[CHAIN_PROPERTY_SET](../../data/oledb/chain-property-set.md)|Grupos de propiedades de cadenas juntos.|  
|[END_PROPERTY_SET](../../data/oledb/end-property-set.md)|Marca el final de un conjunto de propiedades.|  
|[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)|Marca el final de una asignación de conjunto de propiedades.|  
|[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)|Establece una propiedad específica en una propiedad establecida en un valor predeterminado.|  
|[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por el usuario. También permite establecer las opciones y marcas.|  
|[PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por el usuario.|  
  
### <a name="column-map-macros"></a>Macros de asignación de columna  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)|Marca el principio de las entradas de asignación de columna de proveedor.|  
|[END_PROVIDER_COLUMN_MAP](../../data/oledb/end-provider-column-map.md)|Marca el final de las entradas de asignación de columna de proveedor.|  
|[PROVIDER_COLUMN_ENTRY](../../data/oledb/provider-column-entry.md)|Representa una columna específica admitida por el proveedor.|  
|[PROVIDER_COLUMN_ENTRY_GN](../../data/oledb/provider-column-entry-gn.md)|Representa una columna específica admitida por el proveedor. Puede especificar el tamaño de la columna, tipo de datos, precisión, escala y GUID del conjunto de filas de esquema.|  
|[PROVIDER_COLUMN_ENTRY_FIXED](../../data/oledb/provider-column-entry-fixed.md)|Representa una columna específica admitida por el proveedor. Puede especificar el tipo de datos de columna.|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)|Representa una columna específica admitida por el proveedor. Puede especificar el tamaño de columna.|  
|[PROVIDER_COLUMN_ENTRY_STR](../../data/oledb/provider-column-entry-str.md)|Representa una columna específica admitida por el proveedor. Se supone que el tipo de columna es una cadena.|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|Representa una columna específica admitida por el proveedor. Al igual que PROVIDER_COLUMN_ENTRY_LENGTH, pero también le permite especificar el tipo de datos de la columna, así como el tamaño.|  
|[PROVIDER_COLUMN_ENTRY_WSTR](../../data/oledb/provider-column-entry-wstr.md)|Representa una columna específica admitida por el proveedor. Se supone que el tipo de columna es una cadena de caracteres Unicode.|  
  
### <a name="schema-rowset-macros"></a>Macros de conjunto de filas de esquema  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)|Marca el principio de una asignación de esquema.|  
|[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)|Asocia un GUID a una clase.|  
|[END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)|Marca el final de una asignación de esquema.|  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [Referencia de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)
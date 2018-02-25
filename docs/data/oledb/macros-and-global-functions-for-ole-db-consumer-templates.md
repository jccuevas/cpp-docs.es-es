---
title: Macros y funciones globales para las plantillas de consumidor OLE DB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 755762e8b77cee9603074fdc8050d227fbd2eeb1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Macros y funciones globales para las plantillas de consumidor OLE DB
Las plantillas de consumidor OLE DB se incluyen las siguientes macros y funciones globales:  
  
### <a name="global-functions"></a>Funciones globales  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|Vuelca la información de registro de Error de OLE DB en el dispositivo de volcado de memoria si se devuelve un error.|  
  
### <a name="accessor-map-macros"></a>Macros de mapa de descriptor de acceso  
  
|||  
|-|-|  
|[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)|Marca el principio de una entrada de descriptor de acceso.|  
|[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)|Marca el principio de las entradas de asignación de descriptores de acceso.|  
|[END_ACCESSOR](../../data/oledb/end-accessor.md)|Marca el final de una entrada de descriptor de acceso.|  
|[END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)|Marca el final de las entradas del mapa de descriptor de acceso.|  
  
### <a name="column-map-macros"></a>Macros de asignación de columna  
  
|||  
|-|-|  
|[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)|Marca el principio de las entradas de asignación de columna en la clase de registro de usuario.|  
|[BLOB_ENTRY](../../data/oledb/blob-entry.md)|Se usa para enlazar un objeto binario grande (BLOB).|  
|[BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)|Indica la longitud de la columna de datos BLOB.|  
|[BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)|Indica la longitud y el estado de la columna de datos BLOB.|  
|[BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)|Notifica el estado de la columna de datos BLOB.|  
|[BLOB_NAME](../../data/oledb/blob-name.md)|Se usa para enlazar un objeto binario grande por nombre de columna.|  
|[BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)|Indica la longitud de la columna de datos BLOB.|  
|[BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)|Indica la longitud y el estado de la columna de datos BLOB.|  
|[BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)|Notifica el estado de la columna de datos BLOB.|  
|[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)|Representa una entrada de marcador en el conjunto de filas. Una entrada de marcador es un tipo especial de entrada de la columna.|  
|[COLUMN_ENTRY](../../data/oledb/column-entry.md)|Representa un enlace a una columna concreta de la base de datos.|  
|[COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)|Representa un enlace a la columna concreta de la base de datos. Admite `type`, *longitud*, *precisión*, `scale`, y *estado* parámetros.|  
|[COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)|Representa un enlace a la columna concreta de la base de datos. Admite la *longitud* variable.|  
|[COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)|Representa un enlace a la columna concreta de la base de datos. Admite *estado* y *longitud* parámetros.|  
|[COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)|Representa un enlace a la columna concreta de la base de datos. Admite *precisión* y `scale` parámetros.|  
|[COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)|Representa un enlace a la columna concreta de la base de datos. Admite la *longitud* variable, *precisión* y `scale` parámetros.|  
|[COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)|Representa un enlace a la columna concreta de la base de datos. Admite *estado* y *longitud* variables, *precisión* y `scale` parámetros.|  
|[COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)|Representa un enlace a la columna concreta de la base de datos. Admite la *estado* variable, *precisión* y `scale` parámetros.|  
|[COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)|Representa un enlace a la columna concreta de la base de datos. Admite la *estado* variable.|  
|[COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)|Representa un enlace a una columna concreta de la base de datos. Admite `type` parámetro.|  
|[COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)|Representa un enlace a la columna concreta de la base de datos. Admite `type` y `size` parámetros.|  
|[COLUMN_NAME](../../data/oledb/column-name.md)|Representa un enlace a una columna concreta de la base de datos por nombre.|  
|[COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de tipo de datos, tamaño, precisión, escala, longitud de la columna y estado de la columna.|  
|[COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de longitud de la columna.|  
|[COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de longitud de columna y el estado.|  
|[COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de precisión y escala.|  
|[COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de precisión, escala y columna de longitud.|  
|[COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de precisión, escala, longitud de la columna y estado de la columna.|  
|[COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de precisión, escala y columna de estado.|  
|[COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de estado de la columna.|  
|[COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de tipo de datos.|  
|[COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de tipo de datos, precisión y escala.|  
|[COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de tipo de datos y tamaño.|  
|[COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)|Representa un enlace a una columna concreta de la base de datos por nombre. Admite la especificación de estado de tipo y la columna de datos.|  
|[END_COLUMN_MAP](../../data/oledb/end-column-map.md)|Marca el final de las entradas de asignación de columna.|  
  
### <a name="command-macros"></a>Macros de comandos  
  
|||  
|-|-|  
|[DEFINE_COMMAND](../../data/oledb/define-command.md)|Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Acepta solo los tipos de cadena que coincida con el tipo de aplicación especificado (ANSI o Unicode). Se recomienda que use [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de `DEFINE_COMMAND`.|  
|[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)|Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Es compatible con aplicaciones ANSI y Unicode.|  
  
### <a name="parameter-map-macros"></a>Macros de mapa de parámetro  
  
|||  
|-|-|  
|[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)|Marca el principio de las entradas del mapa de parámetro en la clase de registro de usuario.|  
|[END_PARAM_MAP](../../data/oledb/end-param-map.md)|Marca el final de las entradas de asignación de parámetro.|  
|[SET_PARAM_TYPE](../../data/oledb/set-param-type.md)|Especifica `COLUMN_ENTRY` macros que sigan la `SET_PARAM_TYPE` macro como entrada, salida o entrada/salida.|  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
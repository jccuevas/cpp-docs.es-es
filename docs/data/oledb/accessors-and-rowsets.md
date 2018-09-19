---
title: Los descriptores de acceso y conjuntos de filas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f8dc681e149d54742e4bf5e7ff44afeebe2292eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113102"
---
# <a name="accessors-and-rowsets"></a>Descriptores de acceso y conjuntos de filas

Para establecer y recuperar datos, plantillas OLE DB usan un descriptor de acceso y un conjunto de filas a través de la [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) clase. Esta clase puede controlar varios descriptores de acceso de diferentes tipos.  
  
## <a name="accessor-types"></a>Tipos de descriptor de acceso  

Todos los descriptores de acceso que se derivan de [CAccessorBase](../../data/oledb/caccessorbase-class.md). `CAccessorBase` Proporciona los parámetros y enlace de columna.  
  
En la siguiente ilustración se muestra los tipos de descriptor de acceso.  
  
![Tipos de descriptor de acceso](../../data/oledb/media/vcaccessortypes.gif "vcaccessortypes")  
Clases de descriptor de acceso  
  
- [CAccessor](../../data/oledb/caccessor-class.md) Utilice este descriptor de acceso cuando conozca la estructura del origen de base de datos en tiempo de diseño. `CAccessor` enlaza estáticamente un registro de base de datos, que contiene el búfer, al origen de datos.  
  
- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) utilizar este descriptor de acceso cuando no conoce la estructura de la base de datos en tiempo de diseño. `CDynamicAccessor` las llamadas `IColumnsInfo::GetColumnInfo` para obtener la información de columna de base de datos. Crea y administra un descriptor de acceso y el búfer.  
  
- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) utilizar este descriptor de acceso para controlar los tipos de comando desconocido. Al preparar los comandos, `CDynamicParameterAccessor` puede obtener información de parámetros de la `ICommandWithParameters` interfaz, si el proveedor admite `ICommandWithParameters`.  
  
- [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md), y [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) Use estas clases cuando no tiene conocimiento del esquema de base de datos. `CDynamicStringAccessorA` Recupera los datos como cadenas ANSI; `CDynamicStringAccessorW` recupera los datos como cadenas Unicode.  
  
- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) con esta clase, puede usar cualquier deseado si el proveedor puede convertir el tipo de los tipos de datos. Controla las columnas de resultados y parámetros del comando.  
  
En la tabla siguiente se resume la compatibilidad de los tipos de descriptor de acceso de plantilla OLE DB.  
  
|Tipo de descriptor de acceso|Dinámico|Identificadores de parámetros|Búfer|Varios descriptores de acceso|  
|-------------------|-------------|--------------------|------------|------------------------|  
|`CAccessor`|No|Sí|Usuario|Sí|  
|`CDynamicAccessor`|Sí|No|plantillas OLE DB|No|  
|`CDynamicParameterAccessor`|Sí|Sí|plantillas OLE DB|No|  
|`CDynamicStringAccessor[A,W]`|Sí|No|plantillas OLE DB|No|  
|`CManualAccessor`|Sí|Sí|Usuario|Sí|  
  
## <a name="rowset-types"></a>Tipos de conjuntos de filas  

Las plantillas OLE DB admiten tres tipos de conjuntos de filas (consulte la ilustración anterior): conjuntos de filas simples (implementado por [CRowset](../../data/oledb/crowset-class.md)), conjuntos de filas masivos (implementado por [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) y los conjuntos de filas (se implementa de matriz por [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Captura de los conjuntos de filas único controlar una sola fila cuando `MoveNext` se llama. Conjuntos de filas masiva pueden obtener varios identificadores de fila. Conjuntos de filas de matriz son conjuntos de filas que se pueden acceder mediante la sintaxis de la matriz.  
  
En la siguiente ilustración se muestra los tipos de conjunto de filas.  
  
![Gráfico de RowsetType](../../data/oledb/media/vcrowsettypes.gif "vcrowsettypes")  
Clases de conjunto de filas  
  
[Conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) hacer no acceder a los datos en los datos de almacén pero en su lugar, tener acceso a información sobre el almacén de datos, denominada metadatos. Conjuntos de filas de esquema se usan normalmente en situaciones en las que la estructura de base de datos no se conoce en tiempo de compilación y debe obtenerse en tiempo de ejecución.  
  
## <a name="see-also"></a>Vea también  

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)